<template>
  <div class="todo-header">
    <input type="text" placeholder="请输入你的任务名称，按回车键确认" @keyup.enter="add">
  </div>
</template>

<script>
import {nanoid} from "nanoid"
export default {
  name: 'MyHeader',
  props:['addTodo'],
  methods:{
    add(e){
      if(!e.target.value)return alert('输入不能为空')
      //包装用户输入成一个todo对象
      const todoObj = {id:nanoid(),title:e.target.value,done:false}
      this.addTodo(todoObj)
      e.target.value=" "
    }
  }
}
</script>

<style lang="scss" scoped>
  .todo-header{
    
  >input{width: 100%;height: 37.6px;border-radius: 6px;
    border: 1px solid #ccc;
    padding: 4px 7px;
    font-size: 14px;
  :focus{
    outline: none;
    border-color: rgba(82, 168, 236, 0.8);
    box-shadow: inset 0 1px 1px rgb(0 0 0 / 8%), 0 0 8px rgb(82 168 236 / 60%);
  }}
  }
</style>
