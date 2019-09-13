<template>
  <section class="section home">
    <div class="columns is-mobile">
      <div class="column is-half">
        <div class="home__imageOfMe_container">
          <img :src="imgSrc" class = "home__imageOfMe">
        </div>
      </div>
      <div class="column is-half">
        <p class="home__header"> Борис Тимофеенко </p>
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
  }

  &__imageOfMe_container {
    height: 50vh;
  }

  &__imageOfMe {
    height: 100%;
  }
}
</style>
