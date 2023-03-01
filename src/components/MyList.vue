<template>
  <ul class="todo-main">
    <MyItem v-for="todoObj in todos"
      :key="todoObj.id"
      :todo="todoObj"
      :checkTodo="checkTodo" 
      :deleteTodo="deleteTodo">
    </MyItem>
  </ul>
</template>

<script>
import MyItem from "./MyItem.vue";
export default {
  name: 'MyList',
  components: { MyItem },
  props:['todos','checkTodo','deleteTodo'],
  data() {
    return {
     
    }
  }
}
</script>

<style lang="scss" scoped>
.todo-main{
  margin:16px 0 ;
    border:1px solid #ddd;
    border-radius: 2px;
    padding: 0;;
}
</style>
