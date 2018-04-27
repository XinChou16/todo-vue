<template>
  <div id="app">
  
  <header>
    <h2 class="title">What to do next?</h2>
    <input type="text"
    placeholder="to do now~"
    v-model="input"
    @keydown.enter="addTodo"
    v-focus>
  </header>

  <section class="todos" v-cloak>
    <todo v-for="(todo,index) in todos" 
    :key="index"
    :todo="todo"
    :index="index"
    @delete="delTodo"></todo>
  </section>
  </div>
</template>

<script>
import todo from "./components/todo";

export default {
  data: function() {
    return {
      input: "",
      todos:[{
        text:'111',
        done:false,
      }]
    };
  },
  components: {
    todo
  },
  methods: {
    addTodo() {
      this.todos.push({
        text: this.input,
        done: false,
      })
      this.input=''
      console.log(this.todos);
    },
    delTodo(index) {
      console.log(index);
      this.todos.splice(index,1)
    }
  },

  // custom directives
  directives: {
    focus: {
      inserted: function(el) {
        el.focus(); // 自动聚焦到输入框
      }
    }
  }
};
</script>

<style>
#app {
  font-family: Helvetica, sans-serif;
  text-align: center;
}
.todo {
  margin-top: 20px;
}
[v-cloak] {
  display:none;
}
</style>
