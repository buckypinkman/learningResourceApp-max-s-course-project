<template>
    <ul>
        <learning-resource-list 
        v-for="res in resources" 
        :key="res.id"
        :id="res.id"
        :title="res.title"
        :description="res.description"
        :link="res.link"
        ></learning-resource-list>
    </ul>
</template>

<script>
    import LearningResourceList from './LearningResourceList'

    export default {
        inject: ['resources'],
        components: {
            LearningResourceList
        }
    }
</script>

<style scoped>
    ul {
        list-style: none;
        margin: 0;
        padding: 0;
        margin: auto;
        max-width: 40rem;
    }
</style>