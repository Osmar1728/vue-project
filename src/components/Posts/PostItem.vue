<template>
    <div class="card">
        <span>
            <h4>{{ props.id }}</h4>
            <h4>{{ props.date }}</h4>
        </span>
        <h1>{{ props.title }}</h1>
        <p>{{ props.body }}</p>
    </div>
</template>
<script lang="ts" setup>
import type { IPost } from '@/interfaces/IPost'
    const props = defineProps<IPost>()
</script>

<style scoped>
    .card{
        border-color: red;
    }
</style>