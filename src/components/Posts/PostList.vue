<template>
    <div>
        <!---->
        <PostItem v-bind="post" v-for="(post, index) in PostData" :key="index"/>
    </div>
</template>
<script lang="ts" setup>
    import PostData from '@/data/PostData'
    import PostItem from './PostItem.vue'
</script>
<style scoped></style>