<script setup>
const { data: posts } = await useAsyncData('latest-posts', () =>
  queryContent('/blog')
    .sort({ data: 1 })
    .limit(3)
    .find()
)
</script>

<template>
  <section>
    <h1 class="text-5xl font-bold mt-20">👋🏻 Hello, I'm a Developer!</h1>
    <p class="text-base text-gray-900 p-2 italic">Software Developer @ HackerKernel</p>
  </section>
  <section class="flex flex-col md:flex-row">
    <div class="md:w-3/4">
      <h2 class="text-3xl font-bold mt-8">My Story</h2>
      <p class="text-lg py-2">
        I’m a passionate Flutter Developer with over a year of hands-on experience in building high-performance cross-platform applications. I’ve led multiple projects from scratch and enhanced existing applications with impactful features, consistently delivering clean, scalable, and maintainable code. My expertise spans mobile, web, and desktop platforms, and I’m particularly skilled in GetX, Bloc, Riverpod & Provider state management, MVC & MVVM architecture, and integrating complex features such as barcode scanning, video/audio calling, chat systems, payment gateways, and multilingual support.
      </p>
      <p class="text-lg py-2">
       Currently, I serve as a SDE2 at HackerKernel, guiding junior developers and conducting code reviews across teams. My leadership and technical contributions recently earned me a 10/10 in my performance review. I’ve published a Flutter package called universal_file_viewer and I’m actively maintaining it to support more formats like Excel, CSV, PPT, and web files.
      </p>
      <p class="text-lg py-2">
       I’ve worked on diverse domains such as healthcare, e-commerce (Shopify integrations), pharmacy systems, Fintech Apps, and productivity tools like Rise Pathway. I’m also exploring web development with focus on NUXT JS and backend development with a focus on Java (Spring Boot) and Golang to become a more well-rounded full-stack developer.
      </p>
    </div>
    <img src="~/assets/images/side-prof.jpg" class="w-1/2 md:max-w-sm p-8 mx-auto rounded-full" />
  </section>

  <section>
    <h2 class="text-3xl font-bold mt-8">Latest Blog Posts</h2>
    <div class="grid md:grid-cols-3 pt-8 gap-10">
      <Post :posts="posts" />
    </div>
  </section>
</template>
