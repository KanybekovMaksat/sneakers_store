<script setup>
import { onMounted } from 'vue'
import Header from './components/Header.vue'
import CardList from './components/CardList.vue'
// import Drawer from './components/Drawer.vue'

onMounted(() => {})
</script>

<template>
  <!-- <Drawer/> -->
  <div class="bg-white w-4/5 m-auto rounded-xl shadow-xl mt-14">
    <Header />

    <div class="p-10">
      <div class="flex justify-between items-center mb-8">
        <h2 class="text-3xl font-bold">Все кроссовки</h2>

        <div class="flex gap-4">
          <select class="py-2 px-3 border rounded-md outline-none" id="">
            <option value="">По названию🔥</option>
            <option value="">По цене (дешевые💰)</option>
            <option value="">По цене (качественные⚡)</option>
          </select>

          <div class="relative">
            <img class="absolute left-3 top-3" src="/search.svg" alt="" />
            <input
              class="border border-gray-200 rounded-md py-2 pl-12 focus:border-gray-400"
              type="text"
              placeholder="Поиск..."
            />
          </div>
        </div>
      </div>

      <div class="mt-10">
        <CardList :sneakers="items" />
      </div>
    </div>
  </div>
</template>
