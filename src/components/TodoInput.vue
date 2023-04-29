<template>
  <div class="inputBox">
    <input type="text" v-model="newTodoItem" @keyup.enter="onAddTodo" placeholder="할 일을 입력해 주세요.">
    <button @click="onAddTodo" :class="`btnAdd ${newTodoItem.length > 0 ? 'on' : ''}`">등록하기</button>
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
            this.$emit('onAddTodo', item);
            this.newTodoItem = '';
          } else {
            alert('할 일을 입력해 주세요.')
          }
        }
      }
    }
</script>
