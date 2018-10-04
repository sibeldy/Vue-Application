<template>
  <b-container>
      <b-row>

           <b-col md>
              <div class="weather">
                  <h2 class="title"> Weather Report</h2>
                  <hr/>
                  <weather></weather>
              </div>

              <div class="themap">
                 <h2 class="title"> Google Map</h2>
                     <hr/>
                 <gmap></gmap>
              </div>
          </b-col>

          <b-col md>
              <div class="todo">
                <h2 class="title"> To Do List</h2>
                    <hr/>

              <todo-list v-bind:todos="todos"></todo-list>
              <create-todo v-on:create-todo="createTodo"></create-todo>
              </div>
          </b-col>

      </b-row>
  </b-container>
</template>

<script>

import TodoList from './components/TodoList'
import Gmap from './components/Gmap'
import Weather from './components/Weather'

export default {
  name: 'app',
  components: {
    TodoList,
 //   CreateTodo,
    Gmap,
    Weather
  },

data() {
          return {
            todos: [],
          };
        },
        methods: {
          createTodo(newTodo) {
            this.todos.push(newTodo);
          },
        },

};
</script>


<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

body {
  background-color: #FEF5E7; }

.weather, .themap, .todo {

  color: #626567;
  text-align: center;
  background-color: white;

  border: {
    radius: 15px;
    color: white;
    style: solid;
    width: 2px;
  }

  padding: 15px;
  margin: 5px;
  padding-top: 0px;
  margin-top: 20px; }

  .title {
  color: #F39C12;

  font: {
    variant: small-caps;
    style: oblique;
    weight: bold; }
  }

  .desc {
  text-transform: capitalize;
  }

 .search, .hava {
  text-align: center;
  font-size: 20px;
  }

  .todos {
    font-size: 20px;
    color: #626567;
  }

  .img {
    width: 30%;
  }
</style>
