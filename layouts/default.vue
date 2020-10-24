<template>
  <div>
    <AppHeader />
    <Nuxt />
    <AppFooter />
  </div>
</template>

<style lang="scss">
@import url("https://fonts.googleapis.com/css2?family=IBM+Plex+Mono");
@import url('https://rsms.me/inter/inter.css');

:root {
  --logo-font-family: "IBM Plex Mono", monospace;
  --accent: #b8050b;
  --sub-color: #959da5;
  --border-color: #b5bdc4;
}
html,
body {
  margin: 0;
  background: #f9fafa;
  font-family: 'Inter',sans-serif;
}
</style>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({});
</script>