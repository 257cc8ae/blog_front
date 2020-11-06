<template>
  <header>
    <div class="header-main">
      <HamburgerButton />
      <Logo />
      <AppNav :navShow="navShow"></AppNav>
    </div>
  </header>
</template>

<style lang="scss">
header {
  width: 100%;
  height: 69px;
  border-bottom: 1px solid #b5bdc4;
  background: #fff;
  position: fixed;
  top: 0;
  left: 0;

  .header-main {
    width: max-content;
    margin-right: auto;
    margin-left: auto;
    display: flex;
  }
}

@media screen and (max-width: 1020px) {
  header {
    .header-main {
      margin: 0;
      display: flex;
    }
  }
}
</style>

<script>
export default {
  data() {
    return {
      navShow: true,
    };
  },
  created() {
    if (process.client && window.innerWidth <= 1020) {
      this.navShow = false;
    }
  },
};
</script>