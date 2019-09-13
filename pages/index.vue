<template>
  <section class="section home">
    <div class="columns is-mobile">
      <div class="column is-half"></div>
      <div class="column is-half">
        <div class="home__imageOfMe_container">
          <img :src="imgSrc" class = "home__imageOfMe"></div>
        </div>
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
  background-color: black;

  &__imageOfMe_container {
    height: 50vh;
  }

  &__imageOfMe {
    height: 100%;
  }
}
</style>
