<template>
  <section>
    <transition-group name="list" tag="ul">
      <li v-for="(data, idx) in propsData" :key="data">
        {{ data }}
        <button @click="removeTodo(data, idx)" class="removeBtn" type="button">-</button>
      </li>
    </transition-group>
  </section>
</template>

<script>
export default {
  name: 'TodoList',
  props: ['propsData'],

  methods: {
    removeTodo(todoItem, index) {
      this.$emit('removeTodo', todoItem, index); // emit의 첫번째 인자는 받는 인자, 나머지는 적용할 인자
    }
  }
}
</script>

<style>
ul {
  list-style: none;
  padding: 0;
  margin: 0;
  text-align: left;
}

li {
  height: 50px;
  min-height: 50px;
  line-height: 50px;
  margin: 0.6rem 0;
  padding: 0 1rem;
  border: 1px solid #ccc;
  border-radius: 4px;
  background: #fff;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.removeBtn {
  width: 30px;
  height: 30px;
  color: #333;
}

/* transition-group 사용방법 */
.list-enter-active,
.list-leave-active {
  transition: all .6s;
}

.list-enter-from {
  opacity: 0;
  transform: translateY(-20px);
}

.list-leave-to {
  opacity: 0;
  transform: translateY(20px);
}

</style>