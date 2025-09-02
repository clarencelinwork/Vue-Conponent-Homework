<script setup>
import ItemListView from '@/views/ItemList.vue'
import CartListView from '@/views/CartList.vue'
import NotifyToastView from '@/views/NotifyToast.vue'

import { provide, ref } from 'vue'
const itemList = ref([
  {
    id: 1,
    name: '耳罩式藍牙耳機',
    description: '舒適配戴，支援降噪技術',
    price: 2490,
    imgUrl:
      'https://images.unsplash.com/photo-1546435770-a3e426bf472b?q=80&amp;w=2065&amp;auto=format&amp;fit=crop&amp;ixlib=rb-4.1.0&amp;ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
  },
  {
    id: 2,
    name: '耳罩式彩虹耳機',
    description: '舒適配戴，支援降噪技術',
    price: 1380,
    imgUrl:
      'https://images.unsplash.com/photo-1546435770-a3e426bf472b?q=80&amp;w=2065&amp;auto=format&amp;fit=crop&amp;ixlib=rb-4.1.0&amp;ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
  },
  {
    id: 3,
    name: '時尚藍牙耳機',
    description: '舒適配戴，支援降噪技術',
    price: 7990,
    imgUrl:
      'https://images.unsplash.com/photo-1546435770-a3e426bf472b?q=80&amp;w=2065&amp;auto=format&amp;fit=crop&amp;ixlib=rb-4.1.0&amp;ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
  },
  {
    id: 4,
    name: '機械式鍵盤',
    description: '紅軸機械鍵盤，打字手感極佳',
    price: 1890,
    imgUrl:
      'https://images.unsplash.com/photo-1546435770-a3e426bf472b?q=80&amp;w=2065&amp;auto=format&amp;fit=crop&amp;ixlib=rb-4.1.0&amp;ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
  },
  {
    id: 5,
    name: '無線滑鼠',
    description: '靜音按鍵設計，長效電池',
    price: 890,
    imgUrl:
      'https://images.unsplash.com/photo-1546435770-a3e426bf472b?q=80&amp;w=2065&amp;auto=format&amp;fit=crop&amp;ixlib=rb-4.1.0&amp;ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
  },
])

const cartItems = ref([])

const addToCart = (item) => {
  let nowCartItem = cartItems.value.find((cartItem) => cartItem.id === item.id)

  if (!nowCartItem) {
    // 創建新的購物車項目，包含數量
    const newCartItem = { ...item, count: 1 }
    cartItems.value.push(newCartItem)
  } else {
    nowCartItem.count += 1
  }
}

const removeFromCart = (cartItem) => {
  cartItems.value = cartItems.value.filter((item) => item.id !== cartItem.id)
}

const isShowToast = ref(false)
const showToastMessage = ref('')

provide('notify', (message) => {
  isShowToast.value = true
  showToastMessage.value = message
  setTimeout(() => {
    isShowToast.value = false
  }, 2000)
})
</script>

<template>
  <div id="app" class="container py-4">
    <div class="row">
      <!-- 商品列表區 -->
      <div class="col-md-8">
        <ItemListView :itemList="itemList" @emit-item="addToCart" />
      </div>

      <!-- 購物車區 -->
      <div class="col-md-4">
        <CartListView :cartItems="cartItems" @emit-cart-item="removeFromCart" />
      </div>
    </div>

    <NotifyToastView :isShowToast="isShowToast" :showToastMessage="showToastMessage" />
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
