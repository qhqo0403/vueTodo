<template>
  <div class="container">
    <button type="button" class="clearAll" @click="clearTodo">Clear List</button>
  </div>
</template>

<script>
export default {
  name: 'TodoFooter',

  methods: {
    clearTodo() {
      this.$emit('removeAll');
    }
  }
}
</script>

<style>
.container {
  height: 50px;
  padding: 40px 0;
}

.clearAll {
  width: 200px;
  height: 50px;
  line-height: 50px;
  background: #9cb;
  border: none;
  border-radius: 5px;
  color: #fff;
  font-weight: bold;
  font-size: 1.3rem;
}
</style>