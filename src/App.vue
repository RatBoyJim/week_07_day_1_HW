<template>
  <div id="app">
    <form v-on:submit.prevent="addToDo">
      <label for="new-todo">Add a new ToDo:</label>
      <input id="new-todo" type="text" v-model="newToDo">
      <input type="radio" value="true" name="priority" v-model="newToDoPriority">
      <label for="high">High priority</label>
      <input type="radio" value="" name="priority" v-model="newToDoPriority">
      <label for="low">Low priority</label>
      <input type="submit" value="Save new ToDo">
    </form>
    <div class="todo-container">
    <ul>
      <li v-for="(todo, index) in todos"
      :key="index" v-bind:class= "todo.priority ? 'high' : 'low'">
      <span>{{todo.name}}</span>
      <br>
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
        {name: "go shopping", priority: true},
        {name: "shower", priority: false},
        {name: "shave", priority: true}
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
      this.newToDoPriority = ""
    },
    // classObject: function(index){
    //   if (todo.priority === "low priority"){
    //     return "low"
    //   } else {
    //     return "high"
    //   }
    // }
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

.todo-container {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    list-style-type: none;
}

.low {
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
    color:green;
}

.high {
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
    color: red;
}
</style>
