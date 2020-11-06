<template>
  <div class="tags">
    <span v-for="tag in tags" :key="tag">
      <nuxt-link :to="'/tags/' + tag">#{{ tag }}</nuxt-link>
    </span>
  </div>
</template>

<style lang="scss">
.tags {
  a,
  span {
    color: var(--sub-color);
    font-family: var(--logo-font-family);
    margin-right: 5px;
    text-decoration: none;
    &:hover {
      color: #0366d6;
      border-bottom: 1px dashed #0366d6;
    }
  }
}
</style>

<script>
export default {
  props: ["tags"],
};
</script>