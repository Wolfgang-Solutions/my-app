<template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-todo="addTodo"/>
    <Todo v-bind:todos="todos"  v-on:del-todo="deleteTodo"/>
    <router-view/>
  </div>
</template>

<script>
import Header from './components/layout/Header';
import Todos from './components/Todos';
import AddTodo from './components/AddTodo';
import axios from 'axios';
export default {
  name:"app",
  components: {
    Header,
    Todos,
    AddTodo
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id!== id);
    },
    addTodo(newTodo) {     //whole parameter needs to be prased for new item on list
      const {title, completed} = newTodo;

      axios.post('https://jsonplaceholder.typicode.com/todos', {title, completed}) //PARAMETERS from constant
      .then(res => this.todos = [...this.todos, res.data])
      .catch(err => console.log(err));

      //this.todos = [...this.todos, newTodo];  //SPREAD operator
    },
    created(){
      axios.get('https://jsonplaceholder.typicode.com/todos?_limit=10') //will return a promise  [LIMIT SET AS 10]
      .then(res => this.todos = res.data)
      .catch(err => console.log(err));
    }
  }
}
</script>


<style>
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }
  body {
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;
  }
  .btn {
    display: inline-block;
    border: none;
    background: #555;
    color: #fff;
    padding: 7px 20px;
    cursor: pointer;
  }
  .btn:hover {
    background: #666;
  }
</style>
