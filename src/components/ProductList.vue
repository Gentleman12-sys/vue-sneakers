<script setup>
import Product from './Product.vue'

const onClickCart = (item) => {
  alert(`${item.title}: ${item.price} ₽`)
}

defineProps({
  items: Array
})
</script>

<template>
    <div class="grid grid-cols-4 gap-4 mt-4">
      <Product
        v-for="item in items"
        :key="item.id"
        :title="item.title"
        :price="item.price"
        imgUrl="/src/assets/sneakers.png"
        @onClickCart="onClickCart"
      />
    </div>
</template>