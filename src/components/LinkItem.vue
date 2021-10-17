<template>
  <a
    data-link
    target="_blank"
    v-on:click = "handleExtend"
  >
    <span data-button-bg></span>
    <span data-button-label v-text="link.label" />
  </a>
</template>

<script>
export default ({
  name: "LinkItem",
  props: ['link'],
})
</script>
