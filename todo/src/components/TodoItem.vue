<template>
    <div class="todo-item" v-bind:class="{'is-complete':todoInChildren.completed}">
    <p>
      <input type="checkbox" v-on:change="markComplete" v-bind:checked="todoInChildren.completed">
      {{todoInChildren.title}}
      <button @click="$emit('del-todo', todo.id)" class="del">X</button>
      </p>
    </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  data(){
      return {
          todoInChildren: this.todo
      }
  },
  methods: {
    markComplete() {
        this.todoInChildren.completed = !this.todoInChildren.completed; 
      this.$emit('update:todo.completed', !this.todo.completed)
    }
  }
}
</script>

<style scoped>
.todo-item {
    background: #f4f4f4;
    padding: 10px;
    border-bottom: 1px #ccc dotted;
  }
  .is-complete {
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