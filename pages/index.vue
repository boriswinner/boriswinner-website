<template>
  <section class="section home">
    <div class="columns is-mobile">
      <div class="column is-4">
        <div class="home__imageOfMe_container">
          <img :src="imgSrc" class = "home__imageOfMe">
        </div>
      </div>
      <div class="column is-8">
        <p class="home__header"> Борис Тимофеенко </p>
        <p class="home__paragraph"> Какой-то текст</p>
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
      imgSrc: require('@/assets/me.png')
    }
  }
}
</script>

<style lang="scss">

.home {

  &__header {
    font-family: 'Open Sans Condensed', sans-serif;   
    font-size: 48px;    
    color: white; 
    font-weight: 300;
  }

  &__paragraph {
    font-family: 'Open Sans', sans-serif;
    font-weight: 400;
    color: #f2f2f2;
  }

  &__imageOfMe_container {
    height: 50vh;
  }

  &__imageOfMe {
    height: 100%;
  }
}
</style>
