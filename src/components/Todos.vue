<template>
    <div>
        <div v-for="todo in todos" :key="todo.id">
          <TodoItem :todo="todo" v-on:del-todo="$emit('del-todo', todo.id)"/> 
        </div>
    </div>
</template>

<script>
import TodoItem from "./TodoItem"
export default {
    name:"Todos",
    components:{
        TodoItem
    },
    props: ["todos"]

}
</script>

<style>
.todo-item{
    background: #f4f4f4;
    padding: 10px;
    border-bottom: 1px dotted #ccc;
}
.is-complete{
    text-decoration: line-through;
}
.del {
    background: #ff0000;
    color: #fff;
    border: none;
    padding: 5px 9px;
    border-radius: 50%;
    cursor: pointer;
    float: right;
    
  }

</style>
