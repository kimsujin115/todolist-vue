<template>
  <div id="appWrap">
    <TodoHeader></TodoHeader>
    <TodoInput @onAddTodo="onAddTodo"></TodoInput>
    <TodoList v-bind:propsdata="todoItems" @onDeleteTodo="onDeleteTodo" @onDeleteAll="onDeleteAll"></TodoList>
    <TodoFooter></TodoFooter>
  </div>
</template>

<script>
  import TodoHeader from './components/TodoHeader.vue'
  import TodoInput from './components/TodoInput.vue'
  import TodoList from './components/TodoList.vue'
  import TodoFooter from './components/TodoFooter.vue'

  export default {
    data() {
      return {
        todoItems : []
      }
    }, 
    created() {
      if ( localStorage.length > 0 ) {
        for (let i=0; i < localStorage.length; i++) {
          this.todoItems.push(localStorage.key(i))
        }
      }
    },
    methods : {
      onAddTodo(item) {
        localStorage.setItem(item, item); //로컬 스토리지에 데이터 저장
        this.todoItems.push(item);
      },
      onDeleteTodo(item, index) {
        localStorage.removeItem(item);
        this.todoItems.splice(index, 1)
      },
      onDeleteAll() {
        localStorage.clear()
        this.todoItems = []
      }
    }, 
    components : {
      'TodoHeader' : TodoHeader,
      'TodoInput' : TodoInput,
      'TodoList' : TodoList,
      'TodoFooter' : TodoFooter,
    }
  }
</script>

<style>
</style>
