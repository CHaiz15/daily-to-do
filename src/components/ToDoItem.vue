<template>
  <div class="ToDoItem">
    <p class="todo-text">{{todo.text}}</p>
    <div class="delete-btn" @click="deleteItem(todo)">-</div>
  </div>
</template>

<script>
  export default {
    name: "to-do-item",
    props: ['todo'],
    methods: {
      deleteItem(todo) {
        this.$emit('delete', todo)
      }
    }
  }
</script>

<style scoped>
  .ToDoItem {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 50%;
    height: auto;
  }
  .todo-text {
    text-align: center;
    width: 100%;
    background-color: white;
    border: 1px solid lightgrey;
    box-shadow: 1px 1px 1px lightgrey;
    padding: 12px;
    margin-right: 10px;
    font-weight: bolder;
  }
  .delete-btn {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 20px;
    padding: 5px;
    height: 20px;
    cursor: pointer;
    background: #ff7373;
    border-radius: 1px #ce4e4a;
    color: white;
    font-size: 1em;
    font-weight: bolder;
    margin-right: 5px;
  }
  .delete-btn:hover {
    box-shadow: none;
    margin-top: 1px;
    margin-left: 1px;
  }
</style>