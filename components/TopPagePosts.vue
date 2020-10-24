<template>
  <section class="posts">
    <div v-if="posts != null">
      <div v-for="post in posts" :key="post.title" class="post">
        <div v-if="post.thumbnail != ''">
          <img
            v-bind:src="post.thumbnail"
            alt="thumbnail image"
            loading="lazy"
            class="thumbnail"
          />
        </div>
        <div class="tags">
          <span v-for="tag in post.tags" :key="tag[0]"> #{{ tag }} </span>
        </div>
        <h2>
          {{ post.title }}
        </h2>
      </div>
    </div>
  </section>
</template>

<style lang="scss">
.posts {
  width: calc(100% - 40px);
  max-width: 1020px;
  padding: 20px;
  margin-left: auto;
  margin-right: auto;
  background: #ffffff;
  margin-top: 20px;
  .post {
    .thumbnail {
      width: 100%;
    }
  }
}
</style>

<script lang="ts">
import Vue from "vue";
export default Vue.extend({
  data() {
    return {
      posts: null,
    };
  },
  created() {
    fetch("http://localhost:3000")
      .then((response) => {
        return response.json();
      })
      .then((json) => {
        this.posts = json;
      })
      .catch((err) => {
        this.posts = null;
      });
  },
});
</script>