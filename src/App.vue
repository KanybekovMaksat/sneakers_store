<script setup>
import { onMounted, provide, reactive, ref, watch } from 'vue'
import axios from 'axios'
import Header from './components/Header.vue'
import CardList from './components/CardList.vue'
import CartItem from './components/CartItem.vue'
// import Drawer from './components/Drawer.vue'

const sneakers = ref([])

const filters = reactive({
  sortBy: 'title',
  searchQuery: ''
})

const onChangeSelect = (event) => {
  filters.sortBy = event.target.value
}

const onChangeInput = (event) => {
  filters.searchQuery = event.target.value
}

const fetchFavorites = async () => {
  try {
    const { data: favorites } = await axios.get('https://5c782080f150df17.mokky.dev/favorites')

    sneakers.value = sneakers.value.map((sneaker) => {
      const favorite = favorites.find((favorite) => favorite.parentId === sneaker.id)

      if (!favorite) {
        return sneaker
      }

      return {
        ...sneaker,
        isFavorite: true,
        favoriteId: favorite.id
      }
    })
    console.log(sneakers.value)
  } catch (error) {
    console.log(error)
  }
}

const addToFavorite = async (sneaker) => {
  try {
    if (!sneaker.isFavorite) {
      const obj = {
        parentId: sneaker.id
      }
      sneaker.isFavorite = true

      const { data } = await axios.post('https://5c782080f150df17.mokky.dev/favorites', obj)

      sneaker.favoriteId = data.id
    } else {
      sneaker.isFavorite = false
      
      await axios.delete(`https://5c782080f150df17.mokky.dev/favorites/${sneaker.favoriteId}`)
      sneaker.favoriteId = null
    }
  } catch (error) {
    console.log(error)
  }
}

const fetchItems = async () => {
  try {
    const params = {
      sortBy: filters.sortBy
    }
    if (filters.searchQuery) {
      params.title = `*${filters.searchQuery}*`
    }
    const { data } = await axios.get(`https://5c782080f150df17.mokky.dev/items`, {
      params
    })
    sneakers.value = data.map((obj) => ({
      ...obj,
      isFavorite: false,
      favoriteId: null,
      isAdded: false
    }))
  } catch (error) {
    console.log(error)
  }
}

onMounted(async () => {
  await fetchItems()
  await fetchFavorites()
})
watch(filters, fetchItems)

provide('addToFavorite', addToFavorite)
</script>

<template>
  <!-- <Drawer/> -->
  <div class="bg-white w-4/5 m-auto rounded-xl shadow-xl mt-14">
    <Header />

    <div class="p-10">
      <div class="flex justify-between items-center mb-8">
        <h2 class="text-3xl font-bold">Все кроссовки</h2>

        <div class="flex gap-4">
          <select @change="onChangeSelect" class="py-2 px-3 border rounded-md outline-none" id="">
            <option value="title">По названию 🔥</option>
            <option value="price">По цене (дешевые 💰)</option>
            <option value="-price">По качеству ⚡</option>
          </select>

          <div class="relative">
            <img class="absolute left-3 top-3" src="/search.svg" alt="" />
            <input
              @input="onChangeInput"
              class="border border-gray-200 rounded-md py-2 pl-12 focus:border-gray-400"
              type="text"
              placeholder="Поиск..."
            />
          </div>
        </div>
      </div>

      <div class="mt-10">
        <CardList :sneakers="sneakers" @addToFavorite="addToFavorite" />
      </div>
    </div>
  </div>
</template>
