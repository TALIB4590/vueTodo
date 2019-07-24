<template>
  <div id="app">
    <Header/>
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos :todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>
import axios from "axios";
import Todos from "./components/Todos";
import Header from "./components/Header";
import AddTodo from "./components/AddTodo";
import { constants } from 'crypto';
export default {
  name: "app",
  components: {
    Todos,
    Header,
    AddTodo
  },
  data() {
    return {
      todos: []
    }
  },
  methods:{
    deleteTodo(id){
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
      .then(res =>this.todos = this.todos.filter(todo => todo.id !== id)).catch(err => console.log(err))
      
    },
      addTodo(newTodo){
        const {title, complete} = newTodo;
        axios.post("https://jsonplaceholder.typicode.com/todos", {
          title,
          complete
        })
        .then(res => this.todos = [...this.todos, res.data]).catch(err => console.log(err));
  }
  },
  created(){
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=0')
    .then(res => this.todos = res.data )
    .catch(err =>console.log(err));
  }

};
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
.btn{
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}
.btn:hover{
  background: #666;
}
</style>
