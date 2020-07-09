<template>
<div>
    <div v-bind:key="todo.id" v-for="todo in todos">
    <TodotItems v-bind:todo="todos" />
    </div>
</div>    
</template>

<script> 
import TodoItems from './TodoItems.vue'
export default {
    name: "Todos",
    components: {
        TodoItems
    },
    props: ["todos"]
}
</script>

<style scoped>

</style>