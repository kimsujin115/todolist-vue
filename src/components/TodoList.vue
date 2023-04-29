<template>
  <div class="listWrap">
    <div class="btnArea">
      <button class="btnAllDel" @click="onDeleteAll">전체삭제</button>
    </div>
    <ul class="todoList">
      <li v-for="(item, index) in todoItems" :key="item">
        <span>{{ item }}</span>
        <button class="btnDel fas fa-trash" @click="onDelteTodo(item, index)"></button>
      </li>
    </ul>
  </div>
</template>

<script>
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
        onDelteTodo(item, index) {
          if (confirm('할 일을 삭제하시겠습니까?')) {
            localStorage.removeItem(item);
            this.todoItems.splice(index, 1)
          }
        },
        onDeleteAll() {
          localStorage.clear()
          this.todoItems = []
        }
      }
    }
</script>

<style>

</style>