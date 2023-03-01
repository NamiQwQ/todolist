<template>
  <li>
    <label>
      <input type="checkbox" :checked="todo.done" @click="handleCheck(todo.id)"/>
      <span>{{ todo.title }}</span>
    </label>
    <button class="btn btn-danger" @click="handleDelete(todo.id)">删除</button>
  </li>
</template>

<script>
export default {
  name: "MyItem",
  //声名接收todo对象
  props: ['todo','checkTodo','deleteTodo'],
  methods:{
    handleCheck(id){
      //通知app组件把对应对象done值取反
      this.checkTodo(id);
    },
    handleDelete(id){
      if(confirm('确定删除吗')){
        this.deleteTodo(id)
      }
    }
  }
}
</script>

<style lang="scss" scoped>
  li{
    height: 36px;line-height: 36px;padding: 0 5px;border-bottom: solid 1px #ddd;
    >button{
      display: none;
    }
    &:hover{
        background-color: #ddd;
        >button{
          display: block;
        }
    }
  }
  .btn{
    &.btn-danger{
      float: right;
      margin: 3px auto;
      background-color: red;
      color: white;
      border: none;
      border-radius: 4px;
      width: 54px;
      height: 30px;
    }
  }
</style>
