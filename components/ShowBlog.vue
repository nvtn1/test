<template>
  <div id="show-blogs">
    <div
      v-for="(blog, index) of blogs"
      :key="index + 'BlogI'"
      class="single-blog"
    >
      <p v-if="$fetchState.pending">Loading....</p>
      <p v-else-if="$fetchState.error">Error While Fetching Blogs</p>
      <ul>
        <h2>{{ blog.title }}</h2>
        <article>{{ blog.body }}</article>
      </ul>

      aaa
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      blogs: [],
    }
  },
  // created() {
  //   this.$axios
  //     .get('https://jsonplaceholder.typicode.com/posts')
  //     .then(function (data) {
  //       // console.log('data', data)
  //       this.blogs = data.data.slice(0, 10)
  //     })
  // }
  async fetch() {
    try {
      const blogu = await this.$axios.get(
        'https://jsonplaceholder.typicode.com/posts'
      )

      this.blogs = blogu.data.slice(0, 5)
    } catch (error) {}
  },
  methods: {},
}
</script>

<style scoped>
#show-blogs {
  max-width: 800px;
  margin: 0 auto;
}

.single-blog {
  padding: 20px;
  margin: 20px 0;
  box-sizing: border-box;
  background: papayawhip;
}
</style>
