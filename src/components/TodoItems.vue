<template>
    <div>
        <p>To do Item</p>
    </div>
</template>
<script>
export default {
    name: "Todo Items",
    props: ["todo"]
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