<template>
  <todoheader />
  <todoinput @addTodo="addTodo" />
                     <!-- 작명 -->
  <todolist :todoItems="todoItems" @removeTodo="removeTodo" />
              <!-- 작명                                작명 -->
  <todofooter />
</template>

<script>
import todoheader from './components/todoheader.vue'
import todoinput from './components/todoinput.vue'
import todolist from './components/todolist.vue'
import todofooter from './components/todofooter.vue'

export default {
  name:'app',
  components:{
    todoheader,
    todoinput,
    todolist,
    todofooter,
  },
  data(){
    return{
      todoItems:[]
    }
  },
  created(){    
    for(let i=0;i<localStorage.length;i++){
      if(localStorage.key(i) !== 'loglevel:webpack-dev-server'){
        this.todoItems.push(localStorage.key(i));
      }
    }
  },
  methods:{
    addTodo(todoItem){
//todoItem=작명,input.vue의 value값을 가져온것
      localStorage.setItem(todoItem,todoItem)
      this.todoItems.push(todoItem)
    },
    removeTodo(todoItem,index){
      localStorage.removeItem(todoItem)
      this.todoItems.splice(index,1)
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@300&display=swap');
body{
  font-family: 'Roboto', sans-serif;
  background: #f6f6f8;
  text-align: center;
}
*{
  margin: 0;
  padding:0;
}
a:link,a:visited{
  text-decoration: none;
  color:#333;
}
.clearfix:after{
  content: "";
  display: block;
  clear:both;
}
li{
  list-style: none;
}
#app{
  padding:0 20px
}
input{
  border-style:groove;
  widows: 70%;
}
button{
  border-style: groove;
}
.shadow{
  box-shadow: 5px 10px 10px rgba(0,0,0,0.03);
}
</style>