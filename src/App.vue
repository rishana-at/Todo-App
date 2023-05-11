<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <!-- <Sample mssg="Welcome to sample"/> -->
    <!-- <Sample></Sample> -->
    <TodoApp></TodoApp>
    <TodoDone></TodoDone>
  </div>
  <!-- </Sample> -->
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
// import Sample from './components/Sample.vue'
import TodoApp from './components/TodoApp.vue'
import TodoDone from './components/TodoDone.vue';
export default {
  name: 'App',
  components: {
    // HelloWorld,
    // Sample,
    TodoApp,
    TodoDone
  },
data(){
  return{
    // fruits:['apple','banana','jkfrt'],
    // addnew:'',
  }
}

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  /* background-color: aqua; */
  /* -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;*/
} 
</style>
