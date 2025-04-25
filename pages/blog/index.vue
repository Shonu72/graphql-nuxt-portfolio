<script setup>
const { data: posts } = await useAsyncData('posts', () =>
  queryContent('/blog').find()
)
</script>

<template>
  <h1 class="text-3xl my-8">Blog Posts</h1>

  <p class="text-lg mb-8">These are some of my favorite blog posts which is about the technology I use. These are some of my favorite blog posts which is about the technology I use. These are some of my favorite blog posts which is about the technology I use. These are some of my favorite blog posts which is about the technology I use. These are some of my favorite blog posts which is about the technology I use. These are some of my favorite blog posts which is about the technology I use.</p>

  <section class="grid md:grid-cols-3 mt-8 gap-10">
    <Post :posts="posts" />
  </section>
</template>
