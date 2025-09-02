<script setup>
const props = defineProps({
  itemList: { type: Array, required: true },
})

const emit = defineEmits(['emit-item'])
const pass = (item) => {
  emit('emit-item', item)
}
</script>

<template>
  <h2 class="mb-3">商品列表</h2>
  <div class="row">
    <div class="col-md-4 mb-4" v-for="item in props.itemList" :key="item.id">
      <div class="card h-100">
        <img :src="item.imgUrl" class="card-img-top" />
        <div class="card-body">
          <h5 class="card-title">{{ item.name }}</h5>
          <p class="card-text">{{ item.description }}</p>
          <p class="fw-bold text-primary">$ {{ item.price }}</p>
          <button class="btn btn-success w-100" @click="pass(item)">加入購物車</button>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped></style>
