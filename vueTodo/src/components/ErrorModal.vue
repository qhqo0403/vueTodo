<template>
  <div class="modal-mask" @click="$emit('close')"> <!-- close를 발생시킴. // 하위컴포넌트에서 상위컴포넌트로 이벤트 전달 -->
    <div class="modal-wrapper">
      <div class="modal-header">
        <slot name="header"></slot>
      </div>
      <div class="modal-footer">
        <slot name="footer"></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ErrorModal'
}
</script>

<style>
.modal-mask {
  position: fixed;
  left: 0;
  top: 0;
  z-index: 9999;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.7);
}

.modal-wrapper {
  width: 300px;
  padding: 20px 30px;
  background: #fff;
  border-radius: 8px;
  margin: 40px auto;
}

.modal-header {
  color: #f96;
  margin-bottom: 20px;
}

.modal-footer {
  font-size: 1.5rem;
}
</style>