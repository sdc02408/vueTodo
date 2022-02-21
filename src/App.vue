<template>
  <div id="app">
    <section class="todoapp">
      <Header @insertTodo="insertTodo" />
      <Todo :todos="todos"
       @removeTodo="removeTodo"
       @updateDone="updateDone"
       @updateTodo="updateTodo"/>
      <Footer/>
    </section>
  </div>
</template>

<script>
import "./assets/css/main.css";

import Header from "./components/Header.vue";
import Todo from "./components/Todo.vue";
import Footer from "./components/Footer.vue";

export default {
  components: {
    Header,
    Todo,
    Footer
  },
  data() {
    return {
      todos: [
        {
          id: new Date(),
          text: 'vue study',
          isDone: true
        },
        {
          id: new Date() + 1,
          text: 'eat vue',
          isDone : false
        }
    
      ]
    }
  },
  methods: {
        insertTodo(text){
            this.todos = [
                ...this.todos,
                {
                    id: new Date().getTime(),
                    text,
                    isDone: false
                }
            ]
        },
        removeTodo(id) {
              this.todos = this.todos.filter(todo => todo.id !== id);
        },
        updateDone(id){
          const todos= [...this.todos];
          const todo = todos.find(todo => todo.id === id);

          if( todo) {
            todo.isDone = !todo.isDone;
            this.todos = todos;
          }
        },
        updateTodo({id, text}) {
          const todos= [...this.todos];
          const todo = todos.find(todo => todo.id === id);

          if(todo) {
            todo.text = text;
            this.todos = todos;
          }
        }
    }
}
</script>

<style>

</style>
