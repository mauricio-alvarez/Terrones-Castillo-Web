<template>
    <section class="max-w-screen max-w-7xl bg-white mx-auto px-4 sm:px-6 lg:px-8 py-12">
      <h2 class="text-3xl font-bold text-gray-900 mb-8">News and insights</h2>
      <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
        <div v-if="posts.length > 0" class="md:col-span-2">
          <div class="bg-white rounded-lg shadow-md overflow-hidden">
            <img :src="posts[0].image" :alt="posts[0].title" class="w-full h-64 object-cover">
            <div class="p-6">
              <p class="text-sm font-medium text-indigo-600 mb-1">{{ posts[0].category }}</p>
              <h3 class="text-xl font-semibold text-gray-900 mb-2">{{ posts[0].title }}</h3>
              <p class="text-gray-600 mb-4">{{ posts[0].date }}</p>
              <p class="text-gray-700">By {{ posts[0].author }}</p>
            </div>
          </div>
        </div>
        <div v-for="post in posts.slice(1)" :key="post.id" class="bg-gray-100 rounded-lg p-6">
          <p class="text-sm font-medium text-indigo-600 mb-1">{{ post.category }}</p>
          <h3 class="text-lg font-semibold text-gray-900 mb-2">{{ post.title }}</h3>
          <p class="text-gray-600 mb-4">{{ post.date }}</p>
          <p class="text-gray-700">By {{ post.author }}</p>
        </div>
      </div>
      <div class="mt-8 text-center">
        <a href="#" class="text-indigo-600 hover:text-indigo-800 font-medium">
          View all
          <span aria-hidden="true"> →</span>
        </a>
      </div>
    </section>
  </template>
  
  <script>
  import { ref, onMounted } from 'vue'
  import { Client } from '@notionhq/client'
  
  export default {
    setup() {
      const posts = ref([])
  
      const fetchPosts = async () => {
        const notion = new Client({ auth: 'secret_FkbZRqGirrSpTVEwiPVxGIY0aAwmbUHpCUGE7TQ7Kay' })
        const databaseId = 'Blog-ec7dd146aa4144c187b333bf4fd46bef'
  
        try {
          const response = await notion.databases.query({
            database_id: databaseId,
            sorts: [
              {
                property: 'Date',
                direction: 'descending',
              },
            ],
            headers: {
                'X-Requested-With': 'XMLHttpRequest',
            },
            proxy: 'https://cors-anywhere.herokuapp.com/',
          })
  
          posts.value = response.results.map(page => ({
            id: page.id,
            title: page.properties.Title.title[0].plain_text,
            category: page.properties.Category.select.name,
            date: new Date(page.properties.Date.date.start).toLocaleDateString(),
            author: page.properties.Author.rich_text[0].plain_text,
            image: page.properties.Image.files[0]?.file.url || '',
          }))
        } catch (error) {
          console.error('Error fetching posts from Notion:', error)
        }
      }
  
      onMounted(fetchPosts)
  
      return {
        posts
      }
    }
  }
  </script>