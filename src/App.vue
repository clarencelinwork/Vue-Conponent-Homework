<script setup>
import ItemListView from '@/views/ItemList.vue'
import CartView from '@/views/Cart.vue'
import NotifyToastView from '@/views/NotifyToast.vue'
</script>

<template>
  <div id="app" class="container py-4">
    <div class="row">
      <!-- 商品列表區 -->
      <div class="col-md-8">
        <ItemListView />
      </div>

      <!-- 購物車區 -->
      <div class="col-md-4">
        <CartView />
      </div>
    </div>

    <NotifyToastView />
  </div>
</template>

<style scoped>
body {
  background: #f2f2f2f2;
}

.card-img-top {
  height: 150px;
  object-fit: cover;
}
</style>
