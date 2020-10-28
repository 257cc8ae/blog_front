<template>
  <header>
    <button class="mobile-nav-btn">
      <ion-icon name="menu-outline"></ion-icon>
    </button>
    <div class="header-main">
      <div class="logo-area">
        <span class="logo">The Lusaca Blog</span>
      </div>
      <nav>
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
    .logo {
      font-family: var(--logo-font-family);
      line-height: 69px;
      font-size: 20px;
      background: #b8050b;
      color: #fff;
      border-radius: 4px;
      padding: 10px 20px;
      font-weight: bold;
    }
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
    display: flex;
    .mobile-nav-btn {
      display: block;
      background: #fff;
      color: #000;
      flex: 0 0 auto;
      border: none;
      font-size: 20px;
      line-height: 75px;
      width: 69px;
      height: 69px;
      &:focus {
        outline: none;
      }
    }

    .header-main {
      flex: 0 0 auto;
      nav {
        display: none;
      }
    }
  }
}
</style>