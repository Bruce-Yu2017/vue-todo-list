<template>
  <div class="todo-item" v-bind:class="{'is-completed': todo.completed}">
    <p>
      <input type="checkbox" v-on:change="markComplete" v-model="todo.completed">
      {{todo.title}}
      <button class="del" v-on:click="$emit('del-todo', todo.id)" >x</button>
    </p>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  methods: {
    markComplete(e) {
      this.todo.completed = e.target.checked;
    }
  }
};
</script>

<style scoped>
.todo-item {
  background: #f4f4f4;
  border-bottom: 1px #ccc dotted;
  padding: 10px;
}

.is-completed {
  text-decoration: line-through;
}

.del {
  background: #d15d5d;
  color: #000;
  border: none;
  padding: 5px 9px;
  border-radius: 50%;
  cursor: pointer;
  float: right;
}
</style>