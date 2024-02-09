<template>
    <div>
        <!---->
        <button @click="click()">Click</button>
        <PostItem 
            @say-hi="click()"
            v-bind="post" 
            v-for="(post, index) in PostData" 
            :key="index"/>
    </div>
</template>
<script lang="ts" setup>
    import PostData from '@/data/PostData'
    import PostItem from './PostItem.vue'
    const click = () => {
        alert('Hola desde el padre')
    }
</script>
<style scoped></style>