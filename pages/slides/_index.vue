<script>
import fakeDataFromServer from '~/static/fakeDataFromServer.json'
import Slide from '~/components/Slide.vue'

export default {
  components: {
    Slide
  },
  data() {
    return {
      index: this.$route.params.index,
      slides: fakeDataFromServer.slides
    }
  },
  computed: {
    slide() {
      return this.slides.find((el, i) => i + 1 === parseInt(this.index))
    }
  }
}
</script>

<template>
  <section class="app">
    <!-- <Header /> -->
    <Slide :slide="slide" :slides-count="slides.length" />
  </section>
</template>

<style lang="postcss" scoped>
.app {
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
}

.stages {
  @media (orientation: landscape) {
    max-width: 80vw;
    height: 100vh;
  }

  @media (orientation: portrait) {
    width: 100vw;
    height: 80vh;
  }
}
</style>
