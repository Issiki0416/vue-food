<script setup>
import FoodCard from './components/FoodCard.vue'
import { ref } from 'vue'

const foods = ref([
  {
    name: '寿司',
    emoji: '🍣'
  },
  {
    name: 'ハンバーガー',
    emoji: '🍔'
  },
  {
    name: 'ラーメン',
    emoji: '🍜'
  },
  {
    name: 'ピザ',
    emoji: '🍕'
  },
  {
    name: 'カレー',
    emoji: '🍛'
  },
  {
    name: '焼肉',
    emoji: '🥩'
  }
])

const pickedFoodIndex = ref(0)
const newFoodIndex = ref(1)

function pickFood(index) {
  pickedFoodIndex.value = index
  newFoodIndex.value++
}
</script>

<template>
  <main>
    <h1>今日に食べる？</h1>
    <!-- 属性にrefを使いたいのでv-bindを使用 -->
    <FoodCard
      :name="foods[pickedFoodIndex].name"
      :emoji="foods[pickedFoodIndex].emoji"
      @click="pickFood(pickedFoodIndex)"
    />
    <template v-if="newFoodIndex < foods.length">
      <p>VS</p>
      <FoodCard
        :name="foods[newFoodIndex].name"
        :emoji="foods[newFoodIndex].emoji"
        @click="pickFood(newFoodIndex)"
      />
    </template>
  </main>
</template>

<style scoped>
main {
  width: 350px;
  margin: 100px auto;
  text-align: center;
}
</style>
