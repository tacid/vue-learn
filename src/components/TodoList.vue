<template>
    <ol>
        <li v-for="(todo, index) in todos" @click="doneTodo(index)"
            :key="index">
            {{ todo }}
        </li>
    </ol>
</template>

<script>
export default {
    props: ['todos'],
    methods: {
        doneTodo(index){
            this.$emit('delete-todo', index);
        }
    }
}
</script>

<style scoped>
ol {
    text-align: left;
    padding-left: 30%;
}
</style>