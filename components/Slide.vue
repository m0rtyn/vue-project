<script>
import SoundPlayer from '~/components/SoundPlayer.vue'
import SlideChoice from '~/components/SlideChoice.vue'
import SlideVideo from '~/components/SlideVideo.vue'
import TextContent from '~/components/TextContent.vue'
import Controls from '~/components/Controls.vue'

export default {
  name: 'Slide',
  components: {
    Controls,
    SoundPlayer,
    SlideChoice,
    SlideVideo,
    TextContent
  },
  props: {
    slide: { type: Object, required: true },
    slidesCount: { type: Number, required: true }
  }
}
</script>

<template>
  <div class="scene">
    <section class="slide">
      <div v-if="slide.type === 'text'">
        <TextContent :content="slide.html" />
        <SoundPlayer :audio="slide.voice" autoplay />
      </div>
      <div v-if="slide.type === 'video'">
        <SlideVideo :video="slide" />
      </div>
      <div v-if="slide.type === 'choice'">
        <SlideChoice
          :choices="slide.choices"
          :right-choise="slide.right_choise"
        />
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
      :hide-arrows="slide.hide_arrows"
    />
  </div>
</template>

<style lang="postcss" scoped>
.scene {
  width: 100%;
  height: 80%;
  display: flex;
  align-items: flex-start;
  justify-content: center;
  flex-grow: 1;
  flex-wrap: wrap;
  background-color: white;
}

.slide {
  width: 100%;
  flex-grow: 1;
  margin: 0;
  display: flex;
  flex-flow: column nowrap;
  max-height: 100%;

  @media screen and (min-width: 768px) {
    /* margin: 0 64px; */
  }
}

.progressbar {
  width: 80%;
  margin: 16px;
  align-self: flex-end;
}
</style>
