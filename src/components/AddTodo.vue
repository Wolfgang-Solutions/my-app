<template>
    <div>
        <form @submit="addTodo" >
            <input type="text" v-model="title" name="title" placeholder="Add Todo...">
            <input type="submit" value="Submit" class="btn">
        </form>
    </div>
</template>

<script>
//import  uuid  from "uuid";  NOT NEEDED ANYMORE
export default {
    name: "AddTodo",
    data() 
    {
        return {
            title: ''
        }
    },
    methods: 
    {
        addTodo (e) {
            e.preventDefault();
            const  newTodo ={
                //id: uuid.v4(),   ID PROVIDED BY JSON PLACEHOLDER
                title: this.title,
                completed: false
            }
            //Sending up to parent
            this.$emit('add-todo', newTodo); //whole new Todo needs to be parsed as a parameter

            this.title = '';
        }
    }
    }

</script>

<style scoped>
 form {
     display: flex;

 }

input[type="text"] {
    flex: 10;
    padding: 5px;
}

input[type="submit"] {
    flex: 2;
}

</style>