<template>
  <a
    data-link
    :href="link.url"
    target="_blank"
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
