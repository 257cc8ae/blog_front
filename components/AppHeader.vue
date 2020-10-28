<template>
  <header>
    <div class="header-main">
      <button class="mobile-nav-btn">
        <ion-icon name="menu-outline"></ion-icon>
      </button>
      <Logo />
      <nav v-show="true">
        <ul>
          <nuxt-link to="/">
            <li>Home</li>
          </nuxt-link>
          <nuxt-link to="/posts">
            <li>All Posts</li>
          </nuxt-link>
          <nuxt-link to="/tags">
            <li>Tags</li>
          </nuxt-link>
          <nuxt-link to="/">
            <li>About</li>
          </nuxt-link>
        </ul>
      </nav>
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
  .logo-area {
    flex: 0 0 auto;
    width: max-content;
    height: 69px;
    padding: 0 20px;
  }
  nav {
    flex: 0 0 auto;
    width: max-content;
    ul {
      display: flex;
      margin: 0;
      padding: 0 40px;
      font-family: var(--logo-font-family);
      a {
        color: #000;
        line-height: 69px;
        text-decoration: none;
        li {
          flex: 0 0 auto;
          list-style: none;
          margin: 0 10px;
          display: inline;
          &:hover {
            border-bottom: 2px solid var(--accent);
          }
        }
      }
    }
  }
  .mobile-nav-btn {
    display: none;
  }
}

@media screen and (max-width: 1020px) {
  header {
    .header-main {
      margin: 0;
      display: flex;

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

      nav {
        display: none;
        position: fixed;
        top: 70px;
        left: 0;
        width: 100%;
        height: calc(100vh - 70px);
        background: #fff;
        ul {
          display: block;
          padding: 0;
          a {
            width: 100%;
            text-align: center;
            display: block;
            li {
              float: none;
            }
          }
        }
      }
    }
  }
}
</style>

<script>
export default {
  data() {
    return {
      show: true,
    };
  },
  methods: {
    nav() {},
  },
};
</script>