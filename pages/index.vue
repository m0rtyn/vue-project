<script>
import Header from '~/components/Header.vue'
export default {
  components: {
    Header
  }
}
</script>

<template>
  <section class="app">
    <Header />
    <nuxt-link to="/slides/1">Начать игру</nuxt-link>
  </section>
</template>

<style lang="postcss" scoped>
.app {
  height: 100vh;
  display: flex;
  flex-flow: column nowrap;
  align-items: center;
  justify-content: flex-start;
}
</style>
