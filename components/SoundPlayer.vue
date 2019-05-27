<script>
export default {
  name: 'SoundPlayer',
  props: {
    audio: { type: String, required: true },
    autoplay: { type: Boolean, default: false }
  },
  data() {
    return {
      isPlayed: true
    }
  },
  computed: {
    playButtonText() {
      return this.isPlayed ? 'Replay' : 'Play'
    }
  },
  methods: {
    playSound() {
      this.$refs.player.play()
      this.isPlayed = true
    }
  }
}
</script>

<template>
  <div class="sound-player">
    <audio ref="player" :src="audio" :autoplay="autoplay" />
    <b-button @click="playSound">
      {{ playButtonText }}
    </b-button>
  </div>
</template>

<style lang="postcss" scoped>
.sound-player {
  width: auto;
  margin: 16px;
  margin-top: auto;

  @media screen and (min-width: 768px) {
    margin: 0;
    margin-left: auto;
    order: -1;
  }
}
</style>
