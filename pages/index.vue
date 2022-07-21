<template>
  <div>
    <h1 class="blue">Hello World</h1>
    <SBlog />
    <div class="container">
      <h1>List Blog</h1>
      <!-- <add-blog></add-blog> -->
      <Nuxt-link to="/add-blog">Add Blog</Nuxt-link>
      <ShowBlog />
    </div>
  </div>
</template>

<script>
// import AddBlog from './AddBlog.vue'

export default {
  name: 'IndexPage',
  data() {
    return {
      show: false,
    }
  },
}
</script>

<style scoped>
.blue {
  color: blue;
}

.container {
  padding: 15px;
  margin: 10 auto;
  box-sizing: border-box;
  background: peachpuff;
}

.addy {
  padding: 5px;
  margin: 1px 0;
  box-sizing: border-box;
  background: peachpuff;
}
</style>
