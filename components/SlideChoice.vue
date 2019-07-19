<script>
export default {
  name: 'SlideChoice',
  props: {
    choices: { type: Array, required: true },
    rightChoise: { type: String, required: true }
  },
  data() {
    return {
      answer: null,
      isAnswered: false
    }
  },
  computed: {},
  methods: {
    makeChoose(id) {
      this.answer = id
      this.isAnswered = true
    },
    isRightChoise(id) {
      if (id === this.answer) {
        if (this.answer === this.rightChoise) {
          return 'choise-right'
        } else {
          return 'choise-wrong'
        }
      }
    }
  }
}
</script>

<template>
  <div class="choise-slide">
    <h2>На какой сам сядешь?</h2>
    <div class="choises-wrapper">
      <div
        v-for="choise in choices"
        :key="choise.id"
        :class="['choise', isAnswered ? isRightChoise(choise.id) : null]"
        @click="makeChoose(choise.id)"
      >
        <img :src="choise.image" />
      </div>
    </div>
  </div>
</template>

<style lang="postcss" scoped>
.choise-slide {
  padding: 16px;
}

.choises-wrapper {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-wrap: wrap;
  overflow-y: scroll;

  @media screen and (orientation: landscape) {
    flex-wrap: nowrap;
  }

  @media screen and (min-width: 576px) {
    /* flex-direction: row; */
    width: auto;
  }
}

.choise {
  display: flex;
  position: relative;
  padding: 8px;
  max-width: calc(50% - 24px);
  justify-content: center;
  align-items: center;
  flex-shrink: 1;
  flex-grow: 1;
  height: 100%;
  max-height: 50%;
  border: 2px solid var(--gray);
  border-radius: 4px;
  margin: 4px;
  background-color: white;

  @media screen and (min-width: 768px) {
    width: auto;
    margin-bottom: 32px;
    max-width: 20%;
  }

  &:hover {
    opacity: 0.8;
  }

  &-right::after,
  &-wrong::after {
    content: '';
    position: absolute;
    top: 0;
    display: block;
    width: 100%;
    height: 100%;
    border-radius: 4px;
    opacity: 0.3;
  }

  &-right::after {
    background-color: var(--green);
  }

  &-wrong::after {
    background-color: var(--red);
  }
}

h2 {
  width: 100%;
}

img {
  max-width: 100%;
  max-height: 100%;
}
</style>
