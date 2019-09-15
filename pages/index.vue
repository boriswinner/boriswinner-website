<template>
<div>
  <section class="section home">
    <div class="columns">
      <div class="column is-4">
        <div class="home__imageOfMe_container">
          <img :src="imgSrc" class = "home__imageOfMe">
        </div>
      </div>
      <div class="column is-8">
        <p class="home__header"> {{homeTexts.title}} </p>
        <li class="home__paragraph" v-for="advantage in homeTexts.advantages" :key="advantage">{{advantage}}</li>
      </div>      
    </div>
  </section>

  <section class="section projects">
    <p class="projects__header"> {{projectsTexts.title}} </p>
    <div class="columns">
      <div class="column is-half">
        <div v-for="project in projectsTexts.projects" :key="project.name" class="box">
          <p class="projects__header2"> {{project.name}} </p>
          <div class="columns">
            <div class="column is-narrow">
              <img :src="project.imgSrc" class="projects__imageOfProject">
            </div>
            <div class="column">
              <p class="projects__paragraph">{{project.description}}</p>
              <li class="projects__paragraph" v-for="advantage in project.advantages" :key="advantage">{{advantage}}</li>
              <a class="projects__link" v-for="link in project.links" :href="link.url" :key="link.url">{{link.description}}</a>
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
          }
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
  }

  &__imageOfMe_container {
    height: 50vh;
    animation-duration: 2s;
    animation-name: bounceIn;     
  }

  &__imageOfMe {
    height: 100%;
  }
}

.projects {
  background-color: #eae7af;

  &__header {
    font-family: 'Open Sans Condensed', sans-serif;   
    font-size: 48px;    
    color: #160f30; 
    font-weight: 300;
    margin-bottom: 40px;
  }  

  &__header2 {
    font-family: 'Open Sans Condensed', sans-serif;   
    font-size: 36px;    
    color: #160f30; 
    font-weight: 300;
    margin-bottom: 40px;
  }

  &__paragraph {
    font-family: 'Open Sans', sans-serif;
    font-weight: 400;
    color: black;   
  }

  &__link {
    font-family: 'Open Sans', sans-serif;
    font-weight: 700;  
  }  

  &__imageOfProject {
    height: 50vh;
  }      
}
</style>
