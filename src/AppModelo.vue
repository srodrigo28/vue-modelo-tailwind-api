<template>
  <div class="h-screen w-full bg-black text-white flex justify-center items-center gap-3 flex-col">
      <h1 class="text-3xl bg-red-600 p-5 rounded-md">Hello Vue 3 + TailwindCSS</h1>
      <h2 class="text-3xl bg-red-600 p-5 rounded-md">json-server + Axios</h2>

      <div class="mt-5">
          <div 
            class="row bg-slate-900 text-white w-full p-3 m-3 rounded-md hover:bg-slate-700 cursor-pointer"
            v-for="row in todos"
            :key="row.id"
          >
            {{row.id}} - {{ row.title }}
            <!-- 4. passo <pre>{{ todos }}</pre> -->
          </div>
      </div>
  </div>
</template>

<style scoped>

</style>

<script setup>
  import {ref} from 'vue' // 1. passo
  import axios from 'axios'

  const todos = ref() // 2. passo
  axios.get('todo')
  .then( (response) => {
    todos.value = response.data // 3. passo
    console.log(response.data) //teste
  })
</script>