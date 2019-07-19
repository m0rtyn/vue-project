<script>
export default {
  name: 'SoundPlayer',
  props: {
    audio: { type: String, required: true },
    autoplay: { type: Boolean, default: false }
  },
  methods: {
    playSound() {
      this.$refs.player.play()
    }
  }
}
</script>

<template>
  <div class="sound-player">
    <audio ref="player" :src="audio" :autoplay="autoplay" />
    <b-button class="button-play" @click="playSound">
      <font-awesome-icon icon="redo" />
    </b-button>
  </div>
</template>

<style lang="postcss" scoped>
.sound-player {
  width: auto;
  position: absolute;
  padding: 8px;
  top: 0;
  right: 0;

  @media screen and (min-width: 768px) {
    margin: 0;
    margin-left: auto;
    order: -1;
  }
}

.button-play {
  font-size: 1.5rem;
  padding: 8px;
  line-height: 1;
  border-radius: 50%;
}
</style>
