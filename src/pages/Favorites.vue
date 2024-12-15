<script setup>
import axios from 'axios'
import { onMounted, ref } from 'vue'
import CardList from '../components/CardList.vue'

const favorites = ref([])

onMounted(async () => {
  try {
    const { data } = await axios.get('https://4d351d1f3a5c23a2.mokky.dev/favorites')

    favorites.value = data.map((favorite) => favorite.item)
  } catch (err) {
    console.log(err)
  }
})
</script>

<template>
  <h1 class="text-3xl font-bold">Мои закладки</h1>
  <div class="mt-10">
    <CardList :items="favorites" is-favorites />
  </div>
</template>
