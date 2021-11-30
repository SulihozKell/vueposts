<template>
  <div id="app">
    <Post :posts="posts" />
  </div>
</template>

<script>
import Post from "./components/Post.vue"

export default {
  name: "App",
  components: { Post },
  data() {
    return {
      posts: [
        {
          title: 'Post 1',
          body: 'Ez a törzse az első postnak'
        },
        {
          title: 'Post 2',
          body: 'Ez a törzse az második postnak'
        },
        {
          title: 'Post 3',
          body: 'Ez a törzse az harmadik postnak'
        },
        {
          title: 'Post 4',
          body: 'Ez a törzse az negyedik postnak'
        },
      ]
    }
  },
  methods: {
    Changed(e) {
      this.posts.map(function (post) {
        if (post.title != e.original.title) {
          return post
        }
        post.title = e.new.title
        return post
      })
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
