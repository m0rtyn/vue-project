<script>
export default {
  name: 'TextContent',
  props: {
    content: { type: String, default: '' }
  }
}
</script>

<template>
  <p class="text-content">
    {{ content }}
  </p>
</template>

<style lang="postcss" scoped>
.text-content {
  border-radius: 4px;
  padding: 16px;
  flex-grow: 1;
  margin-bottom: 2rem;

  @media screen and (min-width: 768px) {
    padding: 24px 64px;
    min-height: 70%;
    font-size: 1.5em;
  }
}
</style>
