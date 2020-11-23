<template>
  <div id="app">
    <form v-on:submit.prevent="addToDo">
      <label for="new-todo">Add a new ToDo:</label>
      <input id="new-todo" type="text" v-model="newToDo">
      <input type="radio" value="high priority" name="priority" v-model="newToDoPriority">
      <label for="high">High priority</label>
      <input type="radio" value="low priority" name="priority" v-model="newToDoPriority">
      <label for="low">Low priority</label>
      <input type="submit" value="Save new ToDo">
    </form>
    <div class="todo-container">
    <ul>
      <li v-for="(todo, index) in todos"
      :key="index" class="single-todo-high">
      <span>{{todo.name}}</span>
      <br>
      <span>{{todo.priority}}</span>
      </li>

    </ul>
    </div>
  </div>
</template>

<script>

export default {
  data(){
    return{
      todos: [
        {name: "go shopping", priority: "high priority"},
        {name: "shower", priority: "low priority"},
        {name: "shave", priority: "low priority"}
        ],
      newToDo: "",
      newToDoPriority: ""
    }
  },
  methods: {
    addToDo: function(){
      this.todos.push({
        name: this.newToDo,
        priority: this.newToDoPriority
        });
      this.newToDo = ""
    },
    classObject: function(){
      return {
        "single-todo-low": todo.priority == "low priority",
        "single-todo-high": todo.priority == "high priority"
      }
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.single-todo-low {
    display: flex;
    flex-direction: column;
    border: 5px solid green;
    border-radius: 10%;
    background-color: white;
    min-width: 200px;
    max-width: 300px;
    min-height: 68px;
    padding: 10px;
    line-height: 18px;
    margin-bottom: 10px;
    margin-right: 20px;
}

.single-todo-high {
    display: flex;
    flex-direction: column;
    border: 10px solid red;
    border-radius: 10%;
    background-color: white;
    min-width: 200px;
    max-width: 300px;
    min-height: 68px;
    padding: 10px;
    line-height: 18px;
    margin-bottom: 10px;
    margin-right: 20px;
}
</style>
