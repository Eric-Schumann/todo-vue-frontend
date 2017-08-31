<template>
  <div class="col-md-6 col-md-offset-3">
    <ul class="list-group">
      <li v-for="todo in todos"
        class="list-group-item"
        v-bind:class="{
          'text-danger' : !todo.is_completed,
          'text-success' : todo.is_completed}">
        <h3>{{todo.title}}</h3>
        <p>{{todo.body}}</p>
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'todo',
  data () {
    return {
      todos: []
    }
  },
  created() {
    axios.get('http://localhost:3000/api/todos').then(response => {
      this.todos = response.data;
    }).catch(error => {
      console.log(error);
    });
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
