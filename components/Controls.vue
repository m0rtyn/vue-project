<script>
export default {
  name: 'Controls',
  props: {
    slideIndex: { type: Number, required: true },
    slidesCount: { type: Number, required: true },
    hideArrows: { type: Boolean, default: false }
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
      v-if="!isFirstSlide && !hideArrows"
      class="btn btn-prev-slide"
      :to="prevSlidePath"
    >
      <font-awesome-icon icon="chevron-circle-left" />
    </nuxt-link>
    <nuxt-link
      v-if="!isLastSlide && !hideArrows"
      class="btn btn-next-slide"
      :to="nextSlidePath"
    >
      <font-awesome-icon icon="chevron-circle-right" />
    </nuxt-link>
  </div>
</template>

<style lang="postcss" scoped>
.controls {
  width: 100vw;
  display: flex;
  align-self: flex-end;

  @media screen and (min-width: 576px) {
    position: absolute;
  }
}

.btn {
  color: var(--secondary);
  font-size: 3rem;
  line-height: 1;
  border-radius: 50%;

  &-next-slide {
    margin-left: auto;
  }

  &-prev-slide {
    margin-right: auto;
  }
}
</style>
