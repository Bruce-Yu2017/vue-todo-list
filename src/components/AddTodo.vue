<template>
  <form @submit="addTodo">
    <input type="text" placeholder="在这里填写任务" v-model="todo">
    <input type="submit" value="提交" class="btn">
  </form>
</template>

<script>
export default {
  name: 'AddTodo',
  data() {
    return {
      todo: ''
    }
  },
  methods: {
    addTodo(e) {
      e.preventDefault();
      const data = {
        title: this.todo,
        completed: false
      }
      this.$emit('add-todo', data);
      this.todo = '';
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