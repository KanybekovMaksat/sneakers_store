<script setup>
import DrawerHead from './DrawerHead.vue'
import CartItem from './CartItem.vue'
</script>

<template>
  <div class="fixed top-0 left-0 h-full w-full bg-black z-10 opacity-40"></div>
  <div class="bg-white w-96 h-full fixed right-0 top-0 z-20 p-8">
    <DrawerHead />
    <CartItem />
    <CartItem />
    <div class="flex flex-col gap-4 mt-7">
      <div class="flex items-end gap-2">
        <span>Итого:</span>
        <div class="flex-1 border border-dashed"></div>
        <b>12900 руб</b>
      </div>
      <div class="flex items-end gap-2">
        <span>Налог 5%:</span>
        <div class="flex-1 border border-dashed"></div>
        <b>1074 руб</b>
      </div>
      <button
        class="mt-4 transition bg-lime-500 w-full rounded-xl py-3 text-white disabled:bg-slate-300 hover:bg-lime-600 active:bg-lime-700 cursor-pointer"
      >
        Оформить заказ
      </button>
    </div>
  </div>
</template>
