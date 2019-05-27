<script>
export default {
  name: 'Controls',
  props: {
    stage: { type: Number, required: true },
    slidesCount: { type: Number, required: true }
  },
  computed: {
    isLastSlide() {
      return this.stage === this.slidesCount
    },
    isFirstSlide() {
      return this.stage === 0
    }
  },
  methods: {
    slideSwitching(direction) {
      const modifier = direction === 'forward' ? 1 : -1

      return this.$emit('slide-switching', modifier)
    }
  }
}
</script>

<template>
  <div class="controls">
    <b-button
      class="btn btn-prev-slide"
      variant="secondary"
      :disabled="isFirstSlide"
      @click="slideSwitching('backward')"
    >
      {{ '◄' }}
    </b-button>
    <b-button
      class="btn btn-next-slide"
      variant="secondary"
      :disabled="isLastSlide"
      @click="slideSwitching('forward')"
    >
      {{ '►' }}
    </b-button>
  </div>
</template>

<style lang="postcss" scoped>
.btn {
  font-size: 1.5rem;
  padding: 8px 32px;
  position: absolute;
  bottom: 0;
  margin-bottom: 54px;

  @media screen and (min-width: 768px) {
    padding: 8px 16px;
    height: 50%;
    margin: auto;
    font-size: 1.5rem;
    bottom: 16px;
    top: 0;
  }

  &-next-slide {
    right: 0px;
  }

  &-prev-slide {
    left: 0px;
  }
}
</style>
