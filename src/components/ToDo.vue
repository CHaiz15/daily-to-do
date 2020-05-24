<template>
  <main id='main'>
    <h1 class='title'>Daily To-Do List</h1>
    <h3 class='date'>{{new Date(Date.now()).toLocaleString().split(',')[0]}}</h3>
    <div class='box'> 
      <div class='input-box'>
        <input 
          class='todo-input'
          type='text' 
          v-model='todo' 
          v-on:keyup.enter='createNewToDoItem'
          placeholder='Something fun...'
          maxlength='40'
        />
        <div class='add-btn' @click='createNewToDoItem()'>+</div>
      </div>
      <div class='todos-wrapper'>
        <div class='todos'>
        <ToDoItem 
          v-for='todo in todoList'
          :todo='todo'
          @delete='onDeleteItem'
          :key='todo.id'
        />
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import ToDoItem from './ToDoItem.vue'

export default {
  name: 'ToDo',
  components: {
    ToDoItem
  },
  data() {
    return {
      todoList: [],
      todo: '',
    }
  },
  methods: {
    createNewToDoItem() {
      this.todoList.push({ id: Date.now(), text: this.todo});
      this.todo = '';
    },
    onDeleteItem(todo){
      this.todoList = this.todoList.filter(item => item !== todo);
    }
  }
}
</script>

<style scoped>
  #main {
    height: 100vh;
    width: 100vw;
    background: radial-gradient(ellipse at center, #CE4E4A 0%, #CE4E4A 100%);
    display: flex;
    flex-direction: column;
    justify-content: space-evenly;
    align-items: center;
  }
  .title {
    color: rgba(230,230,230,1);
    font-size: 3em;
    font-weight: bold;
    margin: 0;
    padding: 0;
  }
  .date {
    color: rgba(230,230,230,1);
    font-size: 2em;
    font-weight: bold;
    margin: 0;
    padding: 0;
  }
  .todo-input {
    font-size: 1.5em;
    font-weight: bolder;
    margin-right: 10px;
    box-shadow: 1px 3px 10px 0px rgba(0, 0, 0, 0.3)
  }
  .box {
    background: #EFCD76;
    height: 75vh;
    width: 65vw;
    display: flex;
    box-shadow: 1px 3px 20px 0px rgba(0, 0, 0, 0.3);
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
  .input-box {
    height: 10%;
    width: 100%;
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
  }
  .todos-wrapper {
    height: 70%;
    width: 100%;
    overflow: auto;
  }
  .todos {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
  .todos-wrapper::-webkit-scrollbar {
    display: none;
  }
  .add-btn {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 20px;
    padding: 5px;
    height: 20px;
    cursor: pointer;
    background: black;
    border-radius: 1px black;
    color: white;
    font-size: 1em;
    font-weight: bolder;
    margin-right: 5px;
  }
  .add-btn:hover {
    box-shadow: none;
    margin-top: 1px;
    margin-left: 1px;
  }
</style>
