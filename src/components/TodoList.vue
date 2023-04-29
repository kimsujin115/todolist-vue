<template>
  <div class="listWrap">
    <div class="btnArea">
      <button class="btnAllDel" @click="onDeleteAll">전체삭제</button>
    </div>
    <div class="todoListArea">
      <ul class="todoList" v-if="propsdata.length > 0">
        <li v-for="(item, index) in propsdata" :key="item">
          <span>{{ item }}</span>
          <button class="btnDel fas fa-trash" @click="onDeleteTodo(item, index)"></button>
        </li>
      </ul>
      <p class="noDataText" v-else>등록된 할 일이 없습니다.</p>
    </div>
  </div>
</template>

<script>
    export default {
      props: ['propsdata'],
      methods : {
        onDeleteTodo(item, index) {
          if (confirm('할 일을 삭제하시겠습니까?')) {
            this.$emit('onDeleteTodo', item, index);
          }
        },
        onDeleteAll() {
          this.$emit('onDeleteAll')
        }
      }
    }
</script>

<style>

</style>