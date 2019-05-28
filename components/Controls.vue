<script>
export default {
  name: 'Controls',
  props: {
    slideIndex: { type: Number, required: true },
    slidesCount: { type: Number, required: true }
  },
  computed: {
    isLastSlide() {
      return this.slideIndex === this.slidesCount
    },
    isFirstSlide() {
      return this.slideIndex === 1
    },
    nextSlidePath() {
      const nextIndex = this.slideIndex + 1
      return `/slides/${nextIndex}`
    },
    prevSlidePath() {
      const prevIndex = this.slideIndex - 1
      return `/slides/${prevIndex}`
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
    <nuxt-link
      v-if="!isFirstSlide"
      :to="prevSlidePath"
      class="btn btn-prev-slide"
    >
      {{ '◄' }}
    </nuxt-link>
    <nuxt-link
      v-if="!isLastSlide"
      :to="nextSlidePath"
      class="btn btn-next-slide"
    >
      {{ '►' }}
    </nuxt-link>
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
