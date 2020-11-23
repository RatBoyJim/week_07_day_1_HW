<template>
  <div id="app">
    <h1>ToDo List</h1>
    <form v-on:submit.prevent="addToDo">
      <label for="new-todo" ></label>
      <input id="new-todo" type="text" v-model="newToDo" placeholder="Add a new ToDo" required>
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
        {name: "Buy Milk", priority: true},
        {name: "Shower", priority: false},
        {name: "Shave", priority: true}
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
  font-weight: 400;
}

h1 {
  font-weight: 800;
}

input[type=submit] {
    appearance:none;
    -webkit-appearance:none;
    padding:10px;
    border:solid 5px;
    background-color: black;
    color:#fff;
    font-family: inherit;
    font-weight:600;
    border-radius:5px;
    border-color: black;
    margin-left: 10px;
}

input[type=submit]:hover {
    background-color: white;
    color: black;
    border-color: black;
}

.todo-container {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    list-style-type: none;
    justify-content: center;
}

.low {
    display: flex;
    flex-direction: column;
    border: 10px solid green;
    background-color: white;
    width: 800px;
    padding: 10px;
    color:green;
    font-weight: 600;
    font-size: 18pt;

}

.high {
    display: flex;
    flex-direction: column;
    border: 10px solid red;
    background-color: red;
    width: 800px;
    padding: 10px;
    color: white;
    font-weight: 800;
    font-size: 24pt;
}
</style>
