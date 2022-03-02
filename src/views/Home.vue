<template>
  <div class="home">
      <h1>Home</h1>
      <PostList v-if="showPosts" :posts="posts"/>
      <button @click="showPosts = !showPosts">Toggle posts</button>
      <button @click="posts.pop()">Delete a post</button>
  </div>
</template>

<script>
// @ is an alias to /src
import PostList from '@/components/PostList.vue'
import  { ref } from 'vue'


export default {
  name: 'Home',
  components: {
    PostList
  },

  setup() {
    const posts = ref([])
    const error = ref(null)

    const load = async () => {
      try {
        let data = await fetch('http://localhost:3000/posts')
        console.log(data)
      }
      catch (err) {

      }
    }

    const showPosts = ref(true)

    return { posts, showPosts }
  }
}
</script>
