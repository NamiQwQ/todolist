<template>
  <div id="app">
    <div class="todo-container">
      <div class="todo-wrap">
        <MyHeader :addTodo="addTodo"></MyHeader>
        <MyList :todos="todos" :checkTodo="checkTodo" :deleteTodo="deleteTodo"></MyList>
        <MyFooter :todos="todos" :checkAllTodo="checkAllTodo" :clearAllTodo="clearAllTodo"></MyFooter>
      </div>
    </div>
  </div>
</template>

<script>
import MyFooter from '@/components/MyFooter'
import MyHeader from '@/components/MyHeader'
import MyList from '@/components/MyList'
export default {
  name: 'app',
  components: { MyList, MyHeader, MyFooter },
  data() {
    return {
      todos: [
        { id: '001', title: '吃饭', done: true },
        { id: '002', title: '写代码', done: false },
        { id: '003', title: '看电视', done: false }
      ]
    }
  },
  methods:{
    //添加一个todo
    addTodo(todoObj){
      this.todos.unshift(todoObj)
    },
    //勾选或取消勾选一个todo
    checkTodo(id){
      this.todos.forEach((todo)=>{
        if(todo.id===id){
          todo.done=!todo.done
        }
      })
    },
    //删除一个Todo
    deleteTodo(id){
      this.todos=this.todos.filter(todo=>todo.id!==id)
    },
    //全选或取消全选
    checkAllTodo(done){
      this.todos.forEach((todo)=>{
        todo.done = done
      })
    },
    clearAllTodo(){
      this.todos=this.todos.filter((todo)=>{
        return !todo.done
      })
    }
  }
}
</script>

<style lang="scss">
  .todo-container{
    width: 600px;
   margin: 0 auto;
  border: solid rgb(221, 221, 221) 1px;
  border-radius: 5px;
    >.todo-wrap{
      padding: 10px;
    }
  }
</style>
