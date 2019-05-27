<script>
import Header from '~/components/Header.vue'
import Stages from '~/components/Stages.vue'
import fakeDataFromServer from '~/static/fakeDataFromServer.json'

export default {
  components: {
    Header,
    Stages
  },
  data() {
    return {
      fakeDataFromServer: fakeDataFromServer
    }
  }
}
</script>

<template>
  <section class="container">
    <Header />
    <Stages :data-from-server="fakeDataFromServer" />
  </section>
</template>

<style lang="postcss" scoped>
.container {
  /* margin: 0 auto;
  display: flex;
  flex-flow: column;
  justify-content: flex-start;
  align-items: center;
  text-align: center;
  height: 100vh;

  @media screen (min-width: 768px) {
  } */
}
</style>
