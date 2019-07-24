<template>
  <div>
    <form @submit="addTodo">
      <input v-model="title" type="text" name="title" placeholder="Add todo...." />
      <input type="submit" value="submit" class="btn" />
    </form>
  </div>
</template>

<script>
export default {
  name: "AddTodo",
  data() {
    return {
      title: ""
    };
  },
  methods: {
    addTodo(e) {
      e.preventDefault();

      const newTodo = {
        title: this.title,
        complete: false
      };
      this.$emit('add-todo', newTodo);
      this.title = '';
    }
  }
};
</script>

<style scoped>
form {
  display: flex;
}
input[type="text"] {
  flex: 10;
  padding: 5px;
}
</style>
