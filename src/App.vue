<template>
  <div id="app">
    <section class="todoapp">
      <Header @insertTodo="insertTodo"/>
      <Todo :todos="todos"/>
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
        }
    }
}
</script>

<style>

</style>
