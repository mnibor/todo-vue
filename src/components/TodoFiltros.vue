<template>
    <div class="card text-bg-secondary mt-3">
        <div class="card-body d-flex justify-content-between align-items-center">
            <span role="button" @click="filtrar('active')">
                PENDIENTES
            </span>

            <span role="button" @click="filtrar('all')">
                TODOS
            </span>   

            <span role="button" @click="filtrar('complete')">
                COMPLETADOS
            </span>
        </div>
    </div>
</template>

<script>
import { inject } from '@vue/runtime-core'
    export default {
        setup () {
            const estado = inject('estado')
            const filtrar = filtro => {
                estado.value = filtro
            }
            return { filtrar }
        }
    }
</script>

<style lang="scss" scoped>

</style>