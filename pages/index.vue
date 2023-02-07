<template>
<div>
  <section class="section home">
    <div class="columns is-centered">
      <div class="column is-4 is-hidden-mobile">
        <div class="home__imageOfMe_container">
          <img :src="imgSrc" class = "home__imageOfMe">
        </div>
      </div>
      <div class="column is-narrow-desktop">
        <div v-if="$device.isMobile" class="columns is-mobile is-vcentered">
          <div class="column is-3">
            <img v-if="$device.isMobile" :src="imgSrc" class = "home__imageOfMe home__header">
          </div>
          <div class="column">
            <p class="home__header"> {{homeTexts.title}} </p>
          </div>
        </div>
        <p v-if="!$device.isMobile" class="home__header"> {{homeTexts.title}} </p>
        <li class="home__paragraph" v-for="advantage in truncatedAdvantages" :key="advantage">{{advantage}}</li>
        <p v-if="$device.isMobile" @click="isShowAdvantagesOpened = !isShowAdvantagesOpened" class="projects__link">{{showMoreText}}</p>

        <div class="home__contacts-wrapper">
          <b-icon
              class="home__contact-icon"
              icon="phone"
              size="is-large"
              type="is-primary">
          </b-icon>
          <a class="home__contact" :href="'tel:'+phoneNumber">{{phoneNumber}}</a>

          <b-icon
              class="home__contact-icon"
              icon="telegram"
              size="is-large"
              type="is-light">
          </b-icon>
          <a class="home__contact" :href="'https://t.me/'+telegramNick.substr(1)">{{telegramNick}}</a>

          <b-icon
              class="home__contact-icon"
              icon="email"
              size="is-large"
              type="is-light">
          </b-icon>
          <a class="home__contact" :href="'mailto:'+emailAddress">{{emailAddress}}</a>
        </div>

        <div class = "home__buttons-container">
            <b-button tag="a" class="home__button" size="is-medium" icon-left="github-circle" :href="WebsiteSrc">
                Код этого сайта на GitHub
            </b-button>
            <b-button tag="a" class="home__button" size="is-medium" icon-left="book" type="is-link" :href="CvSrc">
                Моё резюме (PDF)
            </b-button>
        </div>
      </div>
    </div>
  </section>

  <section class="section projects">
    <p class="projects__header"> {{projectsTexts.title}} </p>
    <div class="columns is-multiline">
      <div v-for="project in projectsTexts.projects" :key="project.name" class="column is-half is-flex">
        <div class="box projects__box">
          <p class="projects__header2"> {{project.name}} </p>
          <div class="columns">
            <div class="column is-half is-narrow has-text-centered">
              <img :src="project.imgSrc" class="projects__imageOfProject">
            </div>
            <div class="column">
              <p class="projects__paragraph">{{project.description}}</p>
              <li class="projects__paragraph" v-for="advantage in project.advantages" :key="advantage">{{advantage}}</li>
              <div class="projects__links-container">
                <a class="projects__link" v-for="link in project.links" :href="link.url" :key="link.url">{{link.description}}<br></a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</div>
</template>

<script>
// import Card from '~/components/Card'

export default {
  name: 'HomePage',
  components: {
    // Card
  },
  data () {
    return {
      isShowAdvantagesOpened: false,
      imgSrc: require('@/assets/me.png'),
      CvSrc: require('@/assets/cv.pdf'),
      WebsiteSrc: 'https://github.com/boriswinner/boriswinner-website',
      phoneNumber: '+7 (999) 538-48-93',
      telegramNick: '@no_nick',
      emailAddress: 'boriswinner88@gmail.com',
      homeTexts: {
        title: 'Борис Тимофеенко',
        advantages: [
          'Аспирант 1 года обучения в ИТМО',
          'Закончил магистратуру направления "Большие данные и машинное обучение" в ИТМО',
          'Закончил бакалавриат направления "Прикладная математика и информатика" в ДВФУ',
          'Занимаюсь машинным обучением и нейронными сетями. Область интересов: Computer Vision, генеративное искусство',
          'Выполнил 3 исследовательких проекта по сегментации изображений и генерации музыки',
          'Занимаюсь frontend-разработкой. Vue.js, React, Nuxt.js, Next.js, JQuery',
          'Владею языками программирования Python, C/C++, Javascript',
          'Уверенное знание английского (C1-C2 Advanced)',
          'Понимаю алгоритмы и структуры данных',
          'Git, SQL, NativeScript, Firebird, Flask, Telegram-боты',
        ]
      },
      projectsTexts: {
        title: 'Мои проекты',
        projects: [
          {
            name: 'teendok',
            description: 'Планировщик задач для Android, написанный на NativeScript.',
            advantages: [
              'Вид на месяц, неделю, день',
              'Создание событий со временем начала и конца',
              'синхронизация с удалённым сервером',
              'авторизация с использованием Firebase',
              'Раздача прав на календарь другим пользователям',
              'Привязка геолокации на карте к событию',
              'Экспорт календаря с событиями в .ics',
            ],
            imgSrc: require('@/assets/teendok.jpg'),
            links: [
              {
                url: 'https://github.com/boriswinner/teendok',
                description: 'исходный код на GitHub'
              }
            ]
          },
          {
            name: 'RoflanDB',
            description: 'Опыт командной работы. Учебный проект. Простая СУБД, разработанная с нуля на C++. Реализованы базовые команды, такие как CREATE, INSERT, DELETE, SHOW. Покрыта тестами и бенчмарками.',
            imgSrc: require('@/assets/roflandb.jpg'),
            links: [
              {
                url: 'https://github.com/roflan-da/roflandb/',
                description: 'исходный код на GitHub'
              }
            ]
          },
          {
            name: 'Athanatos',
            description: 'Проект с хакатона, написанный вместе с t1meshift. Утилита для бэкапа данных бизнеса с использованием в качестве хранилища компьютеров соотрудников компании. Данные разбиваются на части, каждая часть в нескольких экземплярах загружается на случайные компьютеры компании. Актуальность данных поддерживается автоматически.',
            imgSrc: require('@/assets/athanatos.png'),
            links: [
              {
                url: 'https://github.com/t1meshift/athanatos',
                description: 'исходный код на GitHub'
              }
            ]
          },
          {
            name: 'Raycaster',
            description: 'На первом курсе с другом написали свой 2.5D-движок в духе Wolfenstein 3-D. Использует SDL2 для рендера, поддерживает текстуры, прозрачность, коллизии, разные разрешения экрана и FOV.',
            imgSrc: require('@/assets/raycaster.gif'),
            links: [
              {
                url: 'https://github.com/boriswinner/raycaster/tree/testing',
                description: 'исходный код на GitHub'
              }
            ]
          },
          {
            name: 'Три в ряд',
            description: 'Игра "три в ряд", написанная на JavaScript вместе с ZeroICQ и SergeyZinkovich',
            imgSrc: require('@/assets/3IR.png'),
            links: [
              {
                url: 'https://github.com/ZeroICQ/3IR',
                description: 'исходный код на GitHub'
              },
              {
                url: 'https://zeroicq.github.io/3IR/',
                description: 'играть онлайн'
              }
            ]
          },
          {
            name: 'WBA',
            description: 'Учебный проект - веб-интерфейс для расписания + бэкенд. Серверная часть написана на Python+Flask, в качестве СУБД используется Firebird.',
            imgSrc: require('@/assets/wba.png'),
            links: [
              {
                url: 'https://github.com/boriswinner/wba',
                description: 'исходный код на GitHub'
              },
            ]
          },
          {
            name: 'Крестики-нолики',
            description: 'Учебный проект - адаптивные крестики-нолики на JS. Написан на 1 курсе.',
            imgSrc: require('@/assets/tic.png'),
            links: [
              {
                url: 'https://github.com/https://github.com/boriswinner/Tic-Tac-Toe/wba',
                description: 'исходный код на GitHub'
              },
              {
                url: 'https://boriswinner.github.io/Tic-Tac-Toe/',
                description: 'Играть онлайн'
              },
            ]
          },
          {
            name: 'Решения задач из CATS',
            description: 'Решения задач на программирование (в основном на алгоритмы и структуры данных), написанные за первые курсы обучения в университете.',
            imgSrc: require('@/assets/tasks.png'),
            links: [
              {
                url: 'https://github.com/boriswinner/task-solutions/',
                description: 'исходный код на GitHub'
              },
            ]
          },
        ]
      }
    }
  },
  computed: {
    truncatedAdvantages: function () {
      let numberOfStrings = (this.$device.isMobile && !this.isShowAdvantagesOpened ? 3 : this.homeTexts.advantages.length)
      return this.homeTexts.advantages.slice(0, numberOfStrings)
    },
    showMoreText: function () {
      return (this.isShowAdvantagesOpened ? 'скрыть' : 'Показать ещё...')
    }
  },
}
</script>

<style lang="scss">

.home {
  background-color:#222222;

  @keyframes bounceIn {
    0% {
      transform: scale(0.1);
      opacity: 0.2;
    }
    100% {
      transform: scale(1);
    }
  }

  &__header {
    font-family: 'Open Sans Condensed', sans-serif;
    font-size: 48px;
    color: white;
    font-weight: 300;
    margin-bottom: 40px;
  }

  &__paragraph {
    font-family: 'Open Sans', sans-serif;
    font-weight: 400;
    color: #f2f2f2;
    text-align: justify;
    max-width: 70%;
    @media only screen and (min-width: 0px) and (max-width: 660px) {
      max-width: 100%;
    }    
  }

  &__contacts-wrapper {
    display: flex;
    flex-direction: row;
    align-items: center;
    flex-wrap: wrap;
    margin-top: 40px;

    @media only screen and (min-width: 0px) and (max-width: 660px) {
      flex-direction: column;
    }
  }

  &__contact-icon {
    flex-basis: 15%;
  }

  &__contact {
    font-family: 'Open Sans Condensed', sans-serif;
    font-size: 32px;
    color: white;
    font-weight: 400;
    flex-basis: 85%;

    @media only screen and (min-width: 0px) and (max-width: 660px) {
      font-size: 24px;
    }
  }

  &__contact:hover {
    color: burlywood;
  }

  &__imageOfMe_container {
    height: 50vh;
    animation-duration: 2s;
    animation-name: bounceIn;
  }

  &__imageOfMe {
    max-height: 100%;
  }

  &__buttons-container {
    margin-top: 20px;
  }

  &__button {
    display: inline-block;
    margin: 5px 10px;

    @media only screen and (min-width: 0px) and (max-width: 660px) {
      width: 100%;
      margin: 5px 0px;
    }
  }
}

.projects {
  background-color: #e4e4e4;

  &__box {
    width: 100%;
  }

  &__header {
    font-family: 'Open Sans Condensed', sans-serif;
    font-size: 48px;
    color: #160f30;
    font-weight: 300;
    margin-bottom: 40px;
    text-align: center;
  }

  &__header2 {
    font-family: 'Open Sans Condensed', sans-serif;
    font-size: 36px;
    color: #160f30;
    font-weight: 300;
    margin-bottom: 40px;
    text-align: center;
  }

  &__paragraph {
    font-family: 'Open Sans', sans-serif;
    font-weight: 400;
    color: black;
    text-align: justify;
  }

  &__links-container {
    margin-top: 20px;
  }

  &__link {
    font-family: 'Open Sans', sans-serif;
    font-weight: 700;
  }

  &__imageOfProject {
    max-height: 50vh;
  }
}
</style>
