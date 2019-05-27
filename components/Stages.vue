<script>
import Stage from '~/components/Stage.vue'
import SoundPlayer from '~/components/SoundPlayer.vue'
import ChoiseStage from '~/components/ChoiseStage.vue'
import VideoStage from '~/components/VideoStage.vue'
import TextContent from '~/components/TextContent.vue'
import Controls from '~/components/Controls.vue'

export default {
  name: 'Stages',
  components: {
    Controls,
    Stage,
    SoundPlayer,
    ChoiseStage,
    VideoStage,
    TextContent
  },
  props: {
    dataFromServer: { type: Object, required: true }
  },
  data() {
    return {
      stage: 0
    }
  },
  computed: {
    slide() {
      return this.dataFromServer.slides[this.stage]
    },
    slidesCount() {
      return this.dataFromServer.slides.length - 1
    }
  },
  methods: {
    switchSlide(modifier) {
      this.stage = this.stage + modifier
    }
  }
}
</script>

<template>
  <div class="stages">
    <Stage>
      <template v-if="slide.html" v-slot:html :html="slide.html">
        <TextContent :content="slide.html" />
        <SoundPlayer :audio="slide.voice" autoplay />
      </template>
      <template v-if="slide.video" v-slot:video>
        <VideoStage :video="slide" />
      </template>
      <template v-if="slide.choices" v-slot:choices>
        <ChoiseStage :choices="slide.choices" />
        <SoundPlayer :audio="slide.voice" autoplay />
      </template>
    </Stage>

    <b-progress
      class="progressbar"
      :value="stage"
      :max="slidesCount"
      animated
    ></b-progress>

    <Controls
      :stage="stage"
      :slides-count="slidesCount"
      @slide-switching="switchSlide"
    />
  </div>
</template>

<style lang="postcss" scoped>
.stages {
  width: 100%;
  display: flex;
  align-items: flex-start;
  justify-content: center;
  flex-grow: 1;
  flex-wrap: wrap;
  position: relative;
}

.progressbar {
  width: 80%;
  margin: 16px;
}
</style>
