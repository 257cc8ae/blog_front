<template>
  <nav v-show="navShow" @click="navClickEve()">
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
</template>

<style lang="scss">
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

@media screen and (max-width: 1020px) {
  nav {
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
</style>

<script>
export default {
  props: ["navShow"],
  methods: {
    navClickEve() {
      this.navShow = false;
    },
  },
};
</script>