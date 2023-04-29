<template>
  <div class="listWrap">
    <div class="btnArea">
      <button class="btnAllDel">전체삭제</button>
    </div>
    <ul class="todoList">
      <li v-for="item in todoItems" :key="item">
        <span>{{ item }}</span>
        <button class="btnDel fas fa-trash""></button>
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
    }
</script>

<style>

</style>