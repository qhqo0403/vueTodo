<template>
  <div class="inputBox">
    <input type="text" v-model="newTodoItem" placeholder="할 일을 입력해주세요!">
    <button type="button" class="addBtn" @click="addTodo">+</button>

    <ErrorModal v-if="showModal" @close="showModal = false">
      <template v-slot:header>Wait!</template>
      <template v-slot:footer>
        <p>할 일을 입력해주세요!</p>
        <button class="closeBtn" @click="showModal = false">닫기</button>
      </template>
    </ErrorModal>
  </div>
</template>

<script>
import ErrorModal from './ErrorModal.vue';

export default {
  data() {
    return {
      showModal: false,
      newTodoItem: '',
    }
  },
  methods: {
    addTodo() {
      if (this.newTodoItem.trim()) {
        let value = this.newTodoItem.trim();
        this.$emit('addTodo', value); // 상위컴포넌트 (app.vue)로 addTodo 이벤트에서 저장한 value값을 전달
        this.newTodoItem = '';
      } else {
        this.showModal = true;
      }
    },
    clearList() {
      this.newTodoItem = '';
    }
  },
  components: {
    ErrorModal
  }
}
</script>

<style>
input {
  width: 500px; height: 30px;
  margin-bottom: 30px;
}
button {
  margin-left: 10px;
  width: 30px; height: 35px;
  background: #fff;
  border: 1px solid #555;
  border-radius: 3px;
}
</style>