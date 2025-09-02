<script setup>
const props = defineProps({
  cartItems: { type: Array, required: true },
})
</script>

<template>
  <h2 class="mb-3">購物車</h2>
  <ul class="list-group mb-3">
    <li class="list-group-item d-flex justify-content-between align-items-center" v-for="cartItem in props.cartItems" :key="cartItem.id">
      <div>
        <h6 class="my-0">{{ cartItem.name }}</h6>
        <small class="text-muted">數量：{{ cartItem.count }}</small>
      </div>
      <div>
        <span class="text-muted">${{ cartItem.price }}</span>
        <button class="btn btn-sm btn-outline-danger ms-2">移除</button>
      </div>
    </li>
  </ul>
</template>

<style scoped></style>
