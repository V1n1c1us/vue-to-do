<template>
  <div id="app">
    <el-container>
      <el-header>
         <el-main>
           <cc-todo></cc-todo>
          </el-main>
      </el-header>
    </el-container>
  </div>
</template>

<script>
import CcTodo from './components/Todo.vue'

export default {
  name: 'app',
  components: {
    CcTodo
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
