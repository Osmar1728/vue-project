<template>
    <div class="card">
        <span>
            <h4>{{ props.id }}</h4>
            <h4>{{ props.date }}</h4>
        </span>
        <h1>{{ props.title }}</h1>
        <p>{{ props.body }}</p>
        <button @click="clicked()">Clickme</button>
        <!--<input type="text" v-model="titulo">-->
    </div>
</template>
<script lang="ts" setup>
    import type { IPost } from '@/interfaces/IPost'
    import { ref } from 'vue'

    const props = defineProps<IPost>()
    const emits = defineEmits(['SayHi'])
   /* const titulo = ref('')*/
    /*const copia = props;*/


    //Funciones
    const clicked = () =>{
        alert("Hola desde el hijo")
    }
</script>

<style scoped>
    .card{
        border: 1px solid red;
        padding: 10px;
        margin: 5px;
    }
</style>