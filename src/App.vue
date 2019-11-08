<template>
  <div id="app">
    <input type="text" v-model="todo" @keydown='add($event)'>
    <button @click='add'>+添加待办事项</button>

    <br>
    <hr>
    <h2>进行中</h2>
    <ol>
      <li v-for="(item,index) in todolist " :key='index' v-if='item.checked'>
       <input type='checkbox' v-model='item.checked'>{{item.title}}---<button @click="del(index)">删除</button>
      </li>
    </ol>
    <hr>
    <h2>已完成</h2>
    <ol>
      <li v-for="(item,index) in todolist " :key='index' v-if='!item.checked'>
       <input type='checkbox' v-model='item.checked'>{{item.title}}---<button @click="del(index)">删除</button>
      </li>
    </ol>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      
      msg: 'Welcome to Your Vue.js App',
      todo:'',
      todolist:[],
      
    }
  },
  methods:{
    add(e){
      console.log(e.keyCode)
      if(e.keyCode==13){
        this.todolist.push({title:this.todo,checked:true})
        this.todo=[];
      }
    },
    del(index){
      
      this.todolist.splice(index,1)
      
    }
  }
}
</script>

<style>

 
</style>
