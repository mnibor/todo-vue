<template>
    <h4 class="my-5">TODO DESDE APP</h4>

    <todo-form />
    <todo-list />


</template>

<suspense>
</suspense>

<script>
import { provide, ref, watchEffect } from 'vue'

import TodoForm from './TodoForm.vue'
import TodoList from './TodoList.vue'   

export default {
    components: { TodoForm, TodoList },
    setup(){
        const todos = ref([])
        provide('todos', todos)

        if (localStorage.getItem('todos')) {
            todos.value = JSON.parse(localStorage.getItem('todos'))
        }

        watchEffect(() => {
            // console.log(todos.value.length)
            // console.log(todos.value)
            localStorage.setItem('todos', JSON.stringify(todos.value))
        })
    }
}
</script>

<style>
</style>
