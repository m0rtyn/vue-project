<script>
export default {
  name: 'VideoSlide',
  props: {
    video: { type: Object, required: true }
  }
}
</script>

<template>
  <div class="video-slide">
    <video class="video-player" :autoplay="video.auto" controls>
      <!-- TODO: fix video path from json -->
      <!-- <source :src="video.video" type="video/mp4" /> -->
      <!-- temporary src path -->
      <source src="~/assets/rickroll.mp4" type="video/mp4" />
    </video>
  </div>
</template>

<style lang="postcss" scoped>
.video-slide {
  background-color: lightgray;
  border-radius: 4px;
  margin-bottom: 88px;

  @media screen and (min-width: 576px) {
    padding: 16px;
    margin: 0;
  }
}

video {
  width: 100%;
}
</style>
