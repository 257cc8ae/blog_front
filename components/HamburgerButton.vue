<template>
  <button class="mobile-nav-btn" @click="nav()">
    <ion-icon name="menu-outline"></ion-icon>
  </button>
</template>

<style lang="scss">
.mobile-nav-btn {
  display: none;
}
@media screen and (max-width: 1020px) {
  .mobile-nav-btn {
    flex: 0 0 auto;
    display: block;
    width: 69px;
    height: 69px;
    background: none;
    border: none;
    font-size: 20px;
    &:focus {
      outline: none;
    }
  }
}
</style>

<script>
export default {
  props: ["navShow"],
  methods: {
    nav() {
      this.$emit("navBtnClick");
    },
  },
};
</script>