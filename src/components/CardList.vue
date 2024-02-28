<script setup>
import Card from './Card.vue'

defineProps({
  sneakers: Array
})

const emit = defineEmits(['addToFavorite'])
</script>

<template>
  <div class="grid grid-cols-4 gap-5">
    <Card
      v-for="sneaker in sneakers"
      :key="sneaker.id"
      :id="sneaker.id"
      :title="sneaker.title"
      :price="sneaker.price"
      :imgUrl="sneaker.imageUrl"
      :is-added="false"
      :onClickFavorite="() => emit('addToFavorite', sneaker)"
      :isFavorite="sneaker.isFavorite"
    />
  </div>
</template>
