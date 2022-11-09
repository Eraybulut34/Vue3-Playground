<template>
  <div class="main">
    <h1 class="text-3xl font-bold-underline red bg-red-200 mt-0 w-64 mx-0 flex-auto">Eray</h1>

    <button class="btn bg-green-500 text-bold-underline ml-4 flex-auto" @click="increment">Arttır</button>
    <button class="btn flex-auto bg-red-300" @click="decrement">Azalt</button>

    <button @click="generateFoodChoice">Yemek Seç</button>
    <h1 class="text-4xl text-bold-underline">{{ count }}</h1>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

// reactive state
const count = ref(0)

// functions that mutate state and trigger updates
function increment() {
  count.value++
}
function decrement() {
  count.value--
}

function getAllDAta() {
  return fetch('https://jsonplaceholder.typicode.com/users')
    .then(res => res.json())
    .then(users => {
      console.log(users)
    })
}

const foods = ref(["Arbys","KFC", "Tavuk Dünyası", "Pidem","Green Salad","Carls Jr.","Dürümle","Sbarro","Kayseri Mutfağı","Et İşleri","Sbarro","Popeyes","Kumpir"])

function generateFoodChoice() {
  const randomIndex = Math.floor(Math.random() * foods.value.length)
  alert(foods.value[randomIndex])


}
onMounted(() => {
generateFoodChoice();
  getAllDAta();
  console.log(`The initial count is ${count.value}.`)
})
</script>

<style lang="scss">
////import scss file
* {
  margin: 0px;
}

.main {
  @include main-bg-color(red);
  @include d-flex(column, center, center);
  height: 100vh;
  width: 100vw;
  @include grid-gap(50px);
  @include font-color(white);

}
</style>
