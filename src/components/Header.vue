<template>
  <header class="flex justify-between border-b border-slate-300 px-8 py-4">
    <div class="header-logo flex items-center gap-4">
      <img src="/logo.png" alt="logo" class="w-10 h-10" />
      <div>
        <h2 class="text-xl font-bold uppercase">Sneakers Store</h2>
        <p class="text-slate-500">Магазин лучших кроссовок</p>
      </div>
    </div>

    <nav class="flex items-center gap-10">
      <div
        class="header-cart flex items-center cursor-pointer gap-1 text-gray-500 hover:text-black"
      >
        <img src="/cart.svg" alt="cart" />
        <b>1206 руб</b>
      </div>

      <div
        class="header-favorites flex items-center cursor-pointer gap-1 text-gray-500 hover:text-black"
      >
        <img src="/heart.svg" alt="favorites" />
        <b>Закладки</b>
      </div>

      <div
        class="header-profile flex items-center cursor-pointer gap-1 text-gray-500 hover:text-black c"
      >
        <img src="/profile.svg" alt="profile" />
        <b>Профиль</b>
      </div>
    </nav>
  </header>
</template>
