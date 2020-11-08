<template>
  <div class="search-form-area">
    <form @submit.prevent @submit="SubmitSearch()">
      <input type="text" placeholder="Search..." v-model="word" />
    </form>
  </div>
</template>

<style lang="scss">
.search-form-area {
  input[type="text"] {
    width: calc(100% - 24px);
    padding: 15px 10px;
    font-size: 16.5px;
    border: var(--border-color) solid 2px;
    border-radius: 4px;
    &:focus {
      outline: none;
      border-color: var(--accent);
    }
  }

  input[type="text"]::placeholder {
    color: var(--sub-color);
    font-family: var(--logo-font-family);
  }
}
</style>

<script>
export default {
    data() {
        return {
            word: "",
        }
    },
    methods: {
        SubmitSearch() {
            this.$router.push(`/searches/?q=${this.word}`)            
        }
    }
};
</script>