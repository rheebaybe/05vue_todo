<template>
<section>
   <ul>
      <li v-for="(items,i) in todoItems" :key="i">
        <i class="checkBtn fa fa-check"></i>{{todoItems[i]}}
        <span class="removeBtn" @click="removeTodo(todoItems[i],i)">
          <i class="fa fa-trash"></i>
        </span>
      </li>
    </ul>
</section>
</template>

<script>
export default {
  name:'todolist',
  props:['todoItems'],
  methods:{
    removeTodo(todoItem,index){
      this.$emit('removeTodo',todoItem,index)
    }
  }
}
</script>

<style>
ul{
  text-align: center;
}
li{
  display: flex;
  line-height: 50px;
  margin:0.5rem 0;
  padding:0 1rem;
  background: #fff;
  border-radius: 5px;
}
.checkBtn{
  line-height: 45px;
  color: #62acde;
  margin-right: 5px;
}
.removeBtn{
  margin-left: auto;
  color:#de4343;
}
</style>