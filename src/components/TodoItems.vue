<template>
    <div class="todo-item" v-bind:class="{'is-complete':todo.complete}">
        <p>
            <input type="checkbox" v-on:change="markComplete">
            {{todo.title}}
            <button class="del">x</button>
        </p>
    </div>
</template>
<script>
export default {
    name: "TodoItems",
    props: ["todo"],
    methods:{
        markComplete() {
            console.log(123)
            this.todo.completed = !this.todo.completed;
        }
    }
}
</script>

<style scoped>
.todo-item {
    background-color: antiquewhite;
    padding: 10px;
    border-bottom: 1px #ccc dotted;
}

.is-complete {
    text-decoration: line-through;
}

.del {
    background-color: coral;
    color: #fff;
    border: none;
    padding: 5px 9px;
    border-radius: 50%;
    cursor: pointer;
    float: right;
}
</style>