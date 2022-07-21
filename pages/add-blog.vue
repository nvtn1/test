<template>
  <div id="add-blog">
    <h2>Add A New Blog Post</h2>
    <form v-if="!submitted">
      <label>Blog Title</label>
      <input v-model.lazy="blog.title" type="text" required />
      <label>Blog Content</label>
      <textarea v-model.lazy="blog.content"></textarea>
      <div id="checkboxes">
        <label>Makanan</label>
        <input v-model="blog.categories" type="checkbox" value="Makanan" />
        <label>Minuman</label>
        <input v-model="blog.categories" type="checkbox" value="Minuman" />
        <label>Permainan</label>
        <input v-model="blog.categories" type="checkbox" value="Permainan" />
        <label>Kendaraan</label>
        <input v-model="blog.categories" type="checkbox" value="Kendaraan" />
      </div>
      <label>Author:</label>
      <select v-model="blog.author">
        <option v-for="(author, index) of authors" :key="index + 'BlogA'">
          {{ author }}
        </option>
      </select>
      <button @click.prevent="post">Add Blog</button>
    </form>
    <div v-if="submitted">
      <h3>THanks For Adding A New Post!1!1!1!</h3>
    </div>
    <div id="preview">
      <h3>Preview Blog</h3>
      <p>Blog Title:{{ blog.title }}</p>
      <p>Blog Content:</p>
      <p>{{ blog.content }}</p>
      <p>Blog Categories:</p>
      <ul>
        <li v-for="(category, index) of blog.categories" :key="index + 'blogO'">
          {{ category }}
        </li>
      </ul>
      <p>Author:{{ blog.author }}</p>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      blog: {
        title: '',
        content: '',
        categories: [],
        author: '',
      },
      authors: ['The Dede', 'The Dodoe', 'The Dudude'],
      submitted: false,
    }
  },
  methods: {
    post() {
      try {
        this.$axios.post('https://jsonplaceholder.typicode.com/posts', {
          title: this.blog.title,
          body: this.blog.content,
          userID: 1,
        })
        this.submitted = true
      } catch (error) {}
    },
    // post() {
    //   this.$axios
    //     .post('https://jsonplaceholder.typicode.com/posts', {
    //       title: this.blog.title,
    //       body: this.blog.content,
    //       userID: 1,
    //     })
    //     .then(function (data) {
    //       console.log(data)
    //       this.submitted = true
    //     })
    // },
  },
}
</script>

<style scoped>
#add-blog * {
  box-sizing: border-box;
}

#add-blog {
  margin: 20px auto;
  max-width: 500px;
}
label {
  display: block;
  margin: 20px 0 10px;
}
input[type='text'],
textarea {
  display: block;
  width: 200px;
}
#preview {
  padding: 10px 0 20px;
  border: 1px dotted #ccc;
  margin: 30px 0;
}
h3 {
  margin-top: 10px;
}

#checkboxes input {
  display: inline-block;
  margin-right: 10px;
}

#checkboxes label {
  display: inline-block;
}
</style>
