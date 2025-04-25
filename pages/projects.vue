<script setup>
const query = gql`
{
  viewer {
    repositories(first: 21, orderBy:{field:CREATED_AT,direction: DESC}) {
      totalCount
      nodes {
        id
        name
        createdAt
        description
        url
        forks {
          totalCount
        }
        watchers {
          totalCount
        }
        stargazers {
          totalCount
        }
      }
    }
  }
}
`

const { data } = await useAsyncQuery(query);
</script>

<template>
  <div class="container mx-auto px-4 sm:px-6 lg:px-8 mb-8">
    <h1 class="text-2xl sm:text-3xl md:text-4xl my-6 sm:my-8">Projects</h1>
    <p class="text-base sm:text-2xl mb-2">NOTE - In this page data is fetched from GitHub GraphQL API</p>
    <p class="text-base sm:text-lg mb-6 sm:mb-8">Here are some of my projects on GitHub.</p>
    
    <section class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6 sm:gap-8 md:gap-10">
      <div 
        v-for="project in data?.viewer.repositories.nodes" 
        :key="project.id"
        class="p-6 sm:p-8 border-2 sm:border-4 rounded-lg hover:bg-gray-50 transition-colors duration-200"
      >
        <a :href="project.url" target="_blank" class="group">
          <h2 class="text-xl sm:text-2xl text-indigo-700 md:text-indigo-800 font-semibold mb-2 group-hover:underline ">
            {{ project.name }}
          </h2>
        </a>
        <p class="text-sm sm:text-base">{{ project.description }}</p>
        
        <div class="mt-3 sm:mt-4 flex flex-wrap gap-3 sm:gap-4 text-sm sm:text-base">
          <span class="flex items-center gap-1">
            <Icon name="fontisto:star" size="1rem" class="text-indigo-600 sm:text-indigo-700" /> 
            {{ project.stargazers.totalCount }}
          </span>
          <span class="flex items-center gap-1">
            <Icon name="system-uicons:branch" size="1rem" class="text-indigo-600 sm:text-indigo-800" /> 
            {{ project.forks.totalCount }}
          </span>
          <span class="flex items-center gap-1">
            <Icon name="system-uicons:eye" size="1rem" class="text-indigo-600 sm:text-indigo-700" /> 
            {{ project.watchers.totalCount }}
          </span>
        </div>
      </div>
    </section>
  </div>
</template>