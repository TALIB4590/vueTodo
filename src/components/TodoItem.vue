<template>
  <div class="todo-item" :class="{'is-complete':todo.complete}">
    <p>
        <input type="checkbox" v-on:change="markComplete">
        {{todo.title}}
    <button class="del" @click="$emit('del-todo', todo.id)">X</button>
    </p>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  methods:{
      markComplete(){
          this.todo.complete = !this.todo.complete;
      }
  }
};
</script>

<style>

</style>
