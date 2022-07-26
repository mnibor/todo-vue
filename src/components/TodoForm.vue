<template>
    <div>
        <form @submit.prevent="formulario">
            <input class="form-control my-3" type="text" name="" id="" placeholder="Ingrese la tarea" v-model.trim="texto">
        </form>
    </div>
</template>

<suspense>
</suspense>

<script>
import { inject, ref } from 'vue'

export default {
    setup () {
        const todos = inject('todos')

        const texto = ref('')

        console.log(todos.value)
        const formulario = () => {
            // console.log(texto.value)

            if(texto.value === '') {
                console.log('TEXTO VACIO')
                return
            }

            const todo = {
                texto: texto.value,
                estado: false,
                id: Date.now()
            }

            todos.value.push(todo)

            // console.log(todos.value)

            texto.value = ''
            // console.log(todo)
        }

        

        return {formulario, texto}
    }
}
</script>

<style lang="scss" scoped>

</style>
