<template>
<!-- todo using vue js -->
  <div id="app">
    <v-container>
      <v-layout column>
        <v-flex>
          <v-text-field placeholder="add todo" v-model="text"></v-text-field>
        </v-flex>
        <v-flex>
          <v-btn round @click="addTodo()">create todo</v-btn>
        </v-flex>
      </v-layout>
      <v-layout row wrap>
        <template v-for="(todos,index) in todo">
          <v-flex :key="index">
            <todo :todo="todos"></todo>
          </v-flex>
        </template>
      </v-layout>
    </v-container>
  </div>
</template>
<script>
import Todo from "./components/Todo";
export default {
  name: "HelloWorld",
  components: {
    todo: Todo
  },
  data() {
    return {
      completed: false,
      text: "",
      todo: []
    };
  },
  methods: {
    addTodo() {
      if (this.text == "") {
        alert("please add text");
      } else {
        this.todo.push({
          todo: this.text,
          completed: this.completed,
          deleted: false
        });
        this.text = "";
      }
    }
  }
};
</script>

<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav {
  padding: 30px;
  a {
    font-weight: bold;
    color: #2c3e50;
    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
