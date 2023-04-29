<template>
  <div class="inputBox">
    <input type="text" v-model="newTodoItem" @keyup.enter="onAddTodo" placeholder="할 일을 입력해 주세요.">
    <button @click="onAddTodo" class="btnAdd">등록하기</button>
  </div>
</template>

<script>
    export default {
      data() {

        return {
          newTodoItem : ''
        }
      },
      methods : {
        onAddTodo() {
          if ( this.newTodoItem !== '') {
            const item = this.newTodoItem;
            localStorage.setItem(item, item); //로컬 스토리지에 데이터 저장
            this.newTodoItem = '';

          }
        }
      }
    }
</script>
