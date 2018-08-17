<template>
  <div class="todo">
    <el-row type="flex" justify="center">
        <el-col :span="12">
            <el-input placeholder="Add Tarefa" v-model="tarefa"></el-input>
            <el-button type="primary" icon="el-icon-edit" circle @click="addTarefa"></el-button>
            
        </el-col>
    </el-row>
    <el-row type="flex" justify="center">
        <el-col :span="12">
            <ul>
                <li v-for="tarefa in tarefas" :key="tarefa"> {{ tarefa.title }} ----  <el-button @click="removeTodo(todo)" type="danger" icon="el-icon-delete" circle></el-button></li>
            </ul>
        </el-col>
    </el-row>
  </div>
</template>

<script>
const STORAGE_KEY = 'tarefas-storage';

export default {
  name: 'todo',
  data () {
      return {
          tarefa: "",
          tarefas: []
      }
  },
  created () {
      this.tarefas = JSON.parse(localStorage.getItem(STORAGE_KEY) || '[]')
  },
  methods: {
      addTarefa () {
          this.tarefas.push({
              title: this.tarefa,
              completed: 'false',
              id: this.tarefas.length
          });
          this.tarefa = ''
          localStorage.setItem(STORAGE_KEY, JSON.stringify(this.tarefas));
      },
      removeTodo(todo){
          this.tarefas.splice(this.tarefas.indexOf(todo), 1);
          localStorage.setItem(STORAGE_KEY, JSON.stringify(this.tarefas));
      }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
ul>li {
    list-style: none;
    text-align: justify
}
.el-button[danger]{
    color: red;
}
</style>
