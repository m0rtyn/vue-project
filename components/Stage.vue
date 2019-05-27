<template>
  <div class="stage">
    <slot name="html" />
    <slot name="video" />
    <slot name="choices" />
  </div>
</template>

<script>
export default {
  name: 'Stage'
}
</script>

<style lang="postcss" scoped>
.stage {
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
</style>
