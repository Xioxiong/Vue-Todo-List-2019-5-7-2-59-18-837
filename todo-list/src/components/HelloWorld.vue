<template>
  <div class="todo-list-example">
    <form v-on:submit.prevent="addNewTodo">
      <label for="new-todo">Add a todo</label>
      <input v-model="newTodoText" id="new-todo" placeholder="添加一个选项" />
      <button>Add</button>
    </form>
    <ul>
      <li
        v-for="(todo, index) in todos"
        v-bind:key="todo.id"
        v-bind:title="todo.title"
        v-on:remove="todos.splice(index, 1)"
      ><input type="checkbox" id="checkbox">
         <label for="checkbox">{{ todo.title}}</label>
      </li> 
    </ul>
    
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    
  },
  data() {
    return {
      newTodoText: "",
      todos: [
       
      ],
      nextTodoId: 4
    };
  },
  methods: {
    addNewTodo: function() {
      this.todos.push({
        id: this.nextTodoId++,
        title: this.newTodoText
      });
      this.newTodoText = "";
    },
  },
  mounted: function() {}
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
button {
  margin: 0 20px;
}
li{list-style:none;}
</style>