<template>
  <div>
    <AppHeader />
    <Nuxt />
  </div>
</template>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=IBM+Plex+Mono");
:root {
  --logo-font-family: "IBM Plex Mono", monospace;
  --accent: #b8050b;
}
html,
body {
  margin: 0;
  background: #F9FAFA;
}

</style>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({});
</script>