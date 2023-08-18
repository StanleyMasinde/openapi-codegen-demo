<script setup lang="ts">
import { Ref, onMounted, ref } from 'vue'
import { DefaultApi, Post } from '../generated/index'

const postsAPI = new DefaultApi()
const posts: Ref<Post[]> = ref([])


onMounted(async () => {
  posts.value = await postsAPI.getAllPosts()
  console.log(posts);
})

</script>

<template>
  <main>
    <div class="card" v-for="post in posts">
      <h3>{{ post.title }}</h3>
      <p>{{ post.body }}</p>
    </div>
  </main>
</template>
<style scoped></style>
