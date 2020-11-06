<template>
  <header>
    <div class="header-main">
      <HamburgerButton :navShow="navShow" @navBtnClick="navShowOrHide()" />
      <Logo />
      <AppNav :navShow="navShow" @navLinksClick="navLinkClick()"></AppNav>
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
      navShow: false,
    };
  },
  created() {
    if (process.client && window.innerWidth <= 1020) {
      this.navShow = false;
    } else {
      this.navShow = true;
    }
  },
  methods: {
    navShowOrHide() {
      if (
        process.client &&
        window.innerWidth <= 1020 &&
        this.navShow === false
      ) {
        this.navShow = true;
      } else if (
        process.client &&
        window.innerWidth <= 1020 &&
        this.navShow === true
      ) {
        this.navShow = false;
      }
    },
    navLinkClick() {
      if (process.client && window.innerWidth <= 1020) {
        this.navShow = false;
      };
    },
  },
};
</script>