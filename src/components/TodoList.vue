<template>
    <div>
        <ul class="list-group">
            <todo-item  v-for="todo in todos" :key="todo.id" :todo="todo" />

            <li class="list-group-item list-group-item-success" v-if="todos.length === 0" >No hay elementos...</li>
            <todo-footer v-if="todos.length !== 0" />
        </ul>

    </div>

    <todo-filtros />

</template>

<script>
import { computed, inject, provide, ref } from 'vue'
import TodoItem from './TodoItem.vue'
import TodoFooter from './TodoFooter.vue'
import TodoFiltros from './TodoFiltros.vue'
    export default {
        components: { TodoItem, TodoFooter, TodoFiltros },

        setup () {
            const todosTodos = inject('todos')

            const estado = ref('all')

            const todos = computed(() => {
                if (estado.value === 'all') {
                    return todosTodos.value
                }

                if (estado.value === 'active') {
                    return todosTodos.value.filter(item => item.estado === false)
                }

                if (estado.value === 'complete') {
                    return todosTodos.value.filter(item => item.estado === true)
                }

                return todosTodos.value
            })

            provide('estado', estado)

            return { todos }
        }
        
    }
</script>

<style lang="scss" scoped>

</style>