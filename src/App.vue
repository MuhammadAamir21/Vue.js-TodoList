<template>
  <!-- We can only have one div -->
  <div id="app">
    <Header />
    <!-- Catching the emitted data from AddTodo -->
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>
 <!-- Register any component in the componets sections-->
<script>
import Todos from "./components/Todos";
import AddTodo from "./components/AddTodo";
import Header from "./components/layout/Header";
export default {
  name: "App",
  components: {
    Todos,
    Header,
    AddTodo
  },
  data() {
    //here we return an arrays of objects
    return {
      todos: [
        {
          id: 1,
          title: "Todo One",
          completed: false
        },
        {
          id: 2,
          title: "Todo Two",
          completed: true
        },
        {
          id: 3,
          title: "Todo Three",
          completed: false
        }
      ]
    };
  },
  methods: {
    deleteTodo(id) {
      //her filter loop through like an foreach loop and remove the data related to the id
      this.todos = this.todos.filter(todo => todo.id !== id);
    },
    addTodo(newTodo){
      //Adding the new todo object in the end
      this.todos=[...this.todos,newTodo];

    }
  }
};
</script>

<style>
/* The is global style sheet */
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}
.btn{
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}
.btn.hover{
  background: #666;
}
</style>
