<template>
  <section class="post">
    <div v-if="post != null">
      <img
        v-bind:src="post.thumbnail"
        alt="thumbnail image"
        class="thumbnail"
        loading="lazy"
      />
      <div class="date">
        {{ post.date }}
      </div>
      <h1>{{ post.title }}</h1>
      <div class="tags">
        <span v-for="tag in post.tags" :key="tag[0]" class="tag">
          #{{ tag }}
        </span>
      </div>
      <p v-html="post.content" class="markdown"></p>
    </div>
  </section>
</template>

<style lang="scss">
.post {
  width: calc(100% - 40px);
  max-width: 1020px;
  padding: 20px;
  margin-left: auto;
  margin-right: auto;
  background: #fff;
  margin-top: 20px;
  border-radius: 4px;
  .thumbnail {
    width: 100%;
    border-radius: 4px;
  }

  .date {
    font-family: var(--logo-font-family);
    color: var(--sub-color);
    margin-top: 20px;
  }

  .tags {
    font-family: var(--logo-font-family);
    color: var(--sub-color);
  }

  h1 {
    font-size: 35px;
    margin: 10px 0;
  }
}
.markdown {
  img {
    max-width: 100%;
  }

  .red {
    color: red;
  }

  .iframe-youtube {
    position: relative;
    width: 100%;
    height: 0;
    padding-bottom: 56.25%;
    overflow: hidden;
    margin-bottom: 50px;

    iframe {
      width: 100%;
      height: 100%;
      position: absolute;
      top: 0;
      left: 0;
    }
  }

  .iframe-twitter {
    width: 100%;
    text-align: center;

    iframe {
      width: 100%;
      height: max-content;
      max-width: 550px;
    }
  }

  h1 {
    font-size: 2.5em;
  }

  h2 {
    font-size: 1.5em;
  }

  h3 {
    font-size: 1.2em;
  }

  h4 {
    font-size: 1em;
  }

  h5 {
    font-size: 0.9em;
  }

  h6 {
    font-size: 0.8em;
  }

  .lm-c {
    background: #eee;
    color: #333;
    padding: 2px 5px;
  }

  .hljs {
    border-radius: 4px;
    font-size: 15px;
    background: #1e1e1e;
    color: #dcdcdc;
  }
}
</style>

<script>
export default {
  data() {
    return {
      post: null,
    };
  },
  created() {
    fetch(`http://localhost:3000/posts/${this.$route.params.id}`)
      .then((response) => {
        return response.json();
      })
      .then((json) => {
        this.post = json;
      })
      .catch((err) => {
        this.post = null;
      });
  },
};
</script>