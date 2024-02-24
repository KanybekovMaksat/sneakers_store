<script setup>
defineProps({
  title: String,
  imgUrl: String,
  price: Number,
  isFavorite: Boolean,
  isAdded: Boolean
})
</script>

<template>
  <div
    class="relative bg-white border border-slate-200 rounded-3xl p-8 cursor-pointer transition hover:-translate-y-2 hover:shadow-xl"
  >
    <button class="absolute top-8 left-8">
      <img :src="!isFavorite ? '/like-1.svg' : '/like-2.svg'" alt="like" class="" />
    </button>
    <img :src="imgUrl" alt="Sneaker" />
    <p class="mt-2">{{ title }}</p>
    <div class="flex justify-between mt-5">
      <div class="flex flex-col">
        <span class="text-slate-400">Цена:</span>
        <b>{{ price }} руб.</b>
      </div>
      <img :src="!isAdded ? '/plus.svg' : '/checked.svg'" alt="Plus" />
    </div>
  </div>
</template>
