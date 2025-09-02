<script setup>
const props = defineProps({
  isShowToast: { type: Boolean, required: true },
  showToastMessage: { type: String, required: true },
})
</script>

<template>
  <!-- 通知元件 -->
  <div class="position-fixed top-0 end-0 p-3" style="z-index: 1050" v-if="props.isShowToast">
    <div class="toast show align-items-center text-white bg-success border-0">
      <div class="d-flex">
        <div class="toast-body">{{ props.showToastMessage }}</div>
        <button type="button" class="btn-close btn-close-white me-2 m-auto"></button>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
