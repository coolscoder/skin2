<template>
  <div
    data-extend
    v-for="(extend, index) in this.extends"
    v-bind:key="'et' + index"
  >
    <a
      data-extends
      :href="extend.url"
      target="_blank"
      v-text="extend.label"
    />
  </div>
</template>

<script>
export default ({
  name: "ExtendedItem",
  props: ['extends'],
})
</script>

<style scoped lang="scss">
  [data-extend] {
    width: 100%;
    border-top: 1px solid white;
    color: aqua;
    background-color: rgba($color: #fff, $alpha: 0.2);
  }
</style>
