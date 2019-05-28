<script>
import SoundPlayer from '~/components/SoundPlayer.vue'
import ChoiceSlide from '~/components/ChoiceSlide.vue'
import VideoSlide from '~/components/VideoSlide.vue'
import TextContent from '~/components/TextContent.vue'
import Controls from '~/components/Controls.vue'

export default {
  name: 'Slide',
  components: {
    Controls,
    SoundPlayer,
    ChoiceSlide,
    VideoSlide,
    TextContent
  },
  props: {
    slide: { type: Object, required: true },
    slidesCount: { type: Number, required: true }
  }
}
</script>

<template>
  <div class="slides">
    <section>
      <div v-if="slide.html" class="slide">
        <TextContent :content="slide.html" />
        <SoundPlayer :audio="slide.voice" autoplay />
      </div>
      <div v-if="slide.video" class="slide">
        <VideoSlide :video="slide" />
      </div>
      <div v-if="slide.choices" class="slide">
        <ChoiceSlide :choices="slide.choices" />
        <SoundPlayer :audio="slide.voice" autoplay />
      </div>
    </section>

    <b-progress
      class="progressbar"
      :value="slide.index"
      :max="slidesCount"
      animated
    />

    <Controls
      :slide-index="slide.index"
      :slides-count="slidesCount"
      @slide-switching="switchSlide"
    />
  </div>
</template>

<style lang="postcss" scoped>
.slides {
  width: 100%;
  display: flex;
  align-items: flex-start;
  justify-content: center;
  flex-grow: 1;
  flex-wrap: wrap;
  position: relative;
  background-color: white;
}

.slide {
  width: 100%;
  flex-grow: 1;
  margin: 0;
  display: flex;
  flex-flow: column nowrap;
  height: calc(100% - 54px);

  @media screen and (min-width: 768px) {
    margin: 0 64px;
  }
}

.progressbar {
  width: 80%;
  margin: 16px;
}
</style>
