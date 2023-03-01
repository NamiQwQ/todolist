<template>
  <div class="todo-footer" v-show="total">
    <label>
      <input type="checkbox" :checked="isAll"  @change="checkAll" />
    </label>
    <span>
      <span>已完成{{ doneTotal}}</span> / 全部{{ total }} 
    </span>
    <button @click="clearAll">清除已完成任务</button>
  </div>
</template>

<script>
export default {
  name: 'MyFooter',
  props:['todos','checkAllTodo','clearAllTodo'],
  computed:{
    total(){
      return this.todos.length
    },
    doneTotal(){
      // const x = this.todos.reduce((pre,current)=>{
      //   console.log('@',pre);
      //   return pre + (current.done? 1 : 0)
      // },0)
      return this.todos.reduce((pre,current)=> pre + (current.done? 1 : 0),0)
    },
    isAll(){
      return this.doneTotal===this.total && this.total>0
    }
  },
  methods:{
    checkAll(e){
      this.checkAllTodo(e.target.checked)
      console.log(e.target.checked);
  },
  clearAll(){
    this.clearAllTodo()
  }
}
}
</script>

<style lang="scss" scoped>
  .todo-footer{
    height: 40px;
    line-height: 40px;
    >label{
      margin-right: 20px;
    }
    >button{
      float: right;
      margin: 5px;
      background-color: #da4f49;
      border: solid 1px #bd362f;
      color: white;
      width: 124px;
      height: 30px;
      font-size: 14px;
      border-radius: 4px;
    }
   
  }
</style>
