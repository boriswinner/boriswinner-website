<template>
<div>
  <section class="section home">
    <div class="columns is-centered">
      <div class="column is-4">
        <div class="home__imageOfMe_container">
          <img :src="imgSrc" class = "home__imageOfMe">
        </div>
      </div>
      <b-collapse :open="false" aria-id="show-advantages-button">
      <button
          class="button is-light"
          slot="trigger"
          aria-controls="show-advantages-button">Click me!
      </button>        
      <div class="column is-narrow">
        <p class="home__header"> {{homeTexts.title}} </p>
        <li class="home__paragraph" v-for="advantage in homeTexts.advantages" :key="advantage">{{advantage}}</li>
      </div>      
      </b-collapse>
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
              <a class="projects__link" v-for="link in project.links" :href="link.url" :key="link.url">{{link.description}}<br></a>
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
      imgSrc: require('@/assets/me.png'),
      homeTexts: {
        title: 'Борис Тимофеенко',
        advantages: [
          'Студент 4 курса факультета "Прикладная математика и информатика" ДВФУ',
          'Занимаюсь frontend-разработкой, освоил Vue.JS, Nuxt, Bulma',
          'Занимаюсь мобильной разработкой с использованием NativeScript',
          'Владею языками программирования Python, C/C++, Javascript',
          'Умею пользоваться Git, различными IDE, дебаггером, покрывать код тестами',
          'Имею представление о базах данных (делал учебный проект с использованием Firebird)',
          'Понимаю алгоритмы и структуры данных',
          'Уверенное знание английского (между Upper Intermediate и Advanced)',
          'Создавал Tegegram-ботов на pyTelegramBotAPI',
          'Как-то раз на первом курсе с другом написал 2.5D-движок а-ля Wolfenstein',
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
  }
}
</script>

<style lang="scss">

.home {
  background-color:black;
    
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
  }

  &__imageOfMe_container {
    height: 50vh;
    animation-duration: 2s;
    animation-name: bounceIn;     
  }

  &__imageOfMe {
    max-height: 100%;
  }
}

.projects {
  background-color: #eae7af;

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

  &__link {
    margin-top: 20px;
    display: inline-block;
    font-family: 'Open Sans', sans-serif;
    font-weight: 700;  
  }  

  &__imageOfProject {
    max-height: 50vh;
  }      
}
</style>
