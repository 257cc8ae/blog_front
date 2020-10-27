<template>
  <div class="tag-show">
    <h1>#{{ tag_name }}</h1>
    <p>{{ tag_des }}</p>
    <div v-if="posts != null" class="posts">
      <div v-for="post in posts" :key="post.name">
        <div class="post">
          <div class="date">
            {{ post.date }}
          </div>
          <nuxt-link :to="'/posts/' + post.name">
            <h2>
              {{ post.title }}
            </h2>
          </nuxt-link>
          <div class="tags">
            <span v-for="tag in post.tags.split(' ')" :key="tag[0]" class="tag">
              #{{ tag }}
            </span>
          </div>
        </div>
      </div>
    </div>
    <div v-if="next_page != null">
      <button class="lmp" @click="loadPosts()">Load More Posts</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      posts: null,
      next_page: null,
      tag_des: `Here are article related to ${this.$route.params.id}.`,
      tag_name: this.$route.params.id,
    };
  },
  head() {
    return {
      title: `Hash tag on ${this.$route.params.id} - The Lusaca Blog`,
    };
  },
  created() {
    fetch(`http://localhost:3000/tags/${this.$route.params.id}`)
      .then((response) => {
        return response.json();
      })
      .then((json) => {
        this.posts = json.posts;
        this.next_page = json.next_page;
        this.tag_des = json.descriptions;
        this.tag_name = json.name;
      })
      .catch((err) => {
        this.posts = null;
      });
  },
  methods: {
    loadPosts() {
      fetch(`http://localhost:3000/tags/${this.$route.params.id}?page=${this.next_page}`)
        .then((response) => {
          return response.json();
        })
        .then((json) => {
          this.posts = json.posts;
          this.next_page = json.next_page;
          this.tag_des = json.descriptions;
          this.tag_name = json.name;
        })
        .catch((err) => {
          this.posts = null;
        });
    },
  },
};
</script>

<style lang="scss">
.tag-show {
  width: calc(100% - 40px);
  max-width: 1020px;
  padding: 20px;
  margin-left: auto;
  margin-right: auto;
  background: #fff;
  border-radius: 4px;
  margin-top: 20px;
  h1 {
    font-size: 48px;
    display: inline-block;
    border-bottom: var(--border-color) dashed 1px;
    margin: 10px 0;
  }

  p {
    color: var(--sub-color);
    font-family: var(--logo-font-family);
  }

  .post {
    border-bottom: var(--border-color) dashed 1px;
    padding-bottom: 20px;
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
      margin-top: 10px 0;
    }
    .date {
      font-family: var(--logo-font-family);
      color: var(--sub-color);
      margin-top: 20px;
    }
    .tags {
      .tag {
        color: var(--sub-color);
        font-family: var(--logo-font-family);
      }
    }
  }
  .lmp {
    width: 100%;
    border-radius: 4px;
    border: none;
    background: var(--accent);
    color: #fff;
    font-weight: bold;
    padding: 10px 20px;
    font-size: 20px;
    margin-top: 20px;
    &:focus {
      outline: none;
    }
  }
}
</style>