<template>
  <section class="section home">
    <div class="columns">
      <div class="column is-4">
        <div class="home__imageOfMe_container">
          <img :src="imgSrc" class = "home__imageOfMe">
        </div>
      </div>
      <div class="column is-8">
        <p class="home__header"> {{texts.title}} </p>
        <li class="home__paragraph" v-for="advantage in texts.advantages" :key="advantage">{{advantage}}</li>
      </div>      
    </div>
  </section>
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
      texts: {
        title: 'Борис Тимофеенко',
        description: 'ффффффф',
        advantages: [
          'Студент 4 курса факультета "Прикладная математика и информатика" ДВФУ',
          'Занимаюсь frontend-разработкой, освоил Vue.JS, Nuxt, Bulma',
          'Занимаюсь мобильной разработкой с использованием NativeScript',
          'Владею языками программирования Python, C/C++, Javascript',
          'Умею пользоваться Git, различными IDE, дебаггером, покрывать код тестами',
          'Имею представление о базах данных (делал учебный проект с использованием Firebird)',
          'Уверенное знание английского (между Upper Intermediate и Advanced)',
          'Создавал Tegegram-ботов на pyTelegramBotAPI',
          'Как-то раз на первом курсе с другом написал 2.5D-движок а-ля Wolfenstein',
        ]
      }
    }
  }
}
</script>

<style lang="scss">

.home {
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
</style>
