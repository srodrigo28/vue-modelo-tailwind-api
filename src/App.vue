<template>
  <div class="h-screen w-full bg-black text-white flex justify-center items-center gap-3 flex-col">
      <h1 class="text-3xl bg-blue-600 p-5 rounded-md">Hello Vue 3 + TailwindCSS</h1>

      <div class="mt-5 w-full flex flex-col justify-center items-center">
          <div 
            class=" flex justify-between items-center bg-slate-900 text-white w-96 p-3 m-3 
            rounded-md hover:bg-slate-700 cursor-pointer" v-for="row in todos" :key="row.id" >
              <button v-if="!row.completed" class="bg-red-700 w-8 h-8 rounded-full"> </button>
              <button v-else class="bg-blue-700 w-8 h-8 rounded-full"> </button>
              <p class="text-2xl">{{row.id}} - {{ row.title }}</p>
              <div class="flex gap-2">
                <button @click="updateTodo(row)" class="bg-green-600 p-2 w-25 rounded-md  text-white">Edit</button>
                <button @click="deleteTodo(row.id)" class="bg-red-700   p-2 w-25 rounded-md text-white">Excl</button>
              </div>
            <!-- 4. passo <pre>{{ todos }}</pre> -->
          </div>
      </div>
  </div>
</template>

<script setup>
  import { ref } from 'vue' // 1. passo
  import axios from 'axios'

  const todos = ref() // 2. passo
  
  function listarTodo(){
    axios.get('todo')
    .then( (response) => {
      todos.value = response.data // 3. passo
      console.log(response.data) //teste
    })
  }
  listarTodo()

  function updateTodo(todo){
    const data = {
      completed: !todo.completed
    }
    axios.patch( `todo/${todo.id}`, data)
    .then( (response) => {
      todo.completed = response.data.completed
    })
    .cath(error => (
      // alert('Error')
      console.log('error :( ' + error)
    ))
  }
  function deleteTodo(id){
    axios.delete(`todo/${id}`)
    .then( () => {
      listarTodo()
    })
  }
</script>