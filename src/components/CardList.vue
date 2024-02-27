<script setup>
import Card from './Card.vue'

defineProps({
  sneakers: Array
})
</script>

<template>
  <div class="grid grid-cols-4 gap-5">
    <Card
      v-for="sneaker in sneakers"
      :key="sneaker.id"
      :title="sneaker.title"
      :price="sneaker.price"
      :imgUrl="sneaker.imageUrl"
      :is-added="false"
      :isFavorite="false"
    />
  </div>
</template>
