<template>
  <div class="tags-index">
    <h1>All Tags</h1>
    <div v-if="tags != null">
      <div v-for="tag in tags" :key="tag.name" class="tag">
        <nuxt-link :to="'/tags/' + tag.name">
        <h2>#{{ tag.name }}</h2>
        </nuxt-link>
        <div class="des">
          {{ tag.descriptions }}
        </div>
      </div>
    </div>
    <div v-else>
      <div class="now_loading">Now Loading ...</div>
    </div>
    <div v-if="next_page != null">
      <button class="lmp" @click="loadTags()">Load More Posts</button>
    </div>
  </div>
</template>
<style lang="scss">
.tags-index {
  width: calc(100% - 40px);
  max-width: 1020px;
  padding: 20px;
  margin-left: auto;
  margin-right: auto;
  background: #fff;
  margin-top: 20px;
  border-radius: 4px;
  h1 {
    border-bottom: 1px var(--border-color) dashed;
    display: inline-block;
    font-size: 48px;
  }
  .tag {
    padding: 20px 0;

    a {
      color: #000;
      text-decoration: none;
      &:hover {
        color: #0366d6;
        text-decoration: underline;
      }
    }
    h2 {
      font-size: 28px;
      margin: 10px 0;
    }

    .des {
      font-family: var(--logo-font-family);
      color: var(--sub-color);
    }
  }
  .now_loading {
    color: var(--sub-color);
    font-family: var(--logo-font-family);
    text-align: center;
    font-weight: bold;
  }
}
</style>

<script>
export default {
  data() {
    return {
      tags: null,
      next_page: null,
    };
  },
  methods: {
    loadTags() {
      fetch(`http://localhost:3000/tags?page=${this.next_page}`)
        .then((response) => {
          return response.json();
        })
        .then((json) => {
          let now_tags = this.tags;
          this.tags = now_tags.concat(json.posts);
          this.next_page = json.next_page;
        });
    },
  },
  created() {
    fetch("http://localhost:3000/tags")
      .then((response) => {
        return response.json();
      })
      .then((json) => {
        this.tags = json.tags;
        this.next_page = json.next_page;
      });
  },
};
</script>