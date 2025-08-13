<template>
  <div class="grid grid-cols-2 gap-6 ">
    <div v-for="(hero, index) in project" :key="index" class="bg-white p-4 shadow rounded-xl flex flex-col">
      <div class="w-full h-64 overflow-hidden rounded-lg mb-4">
        <img :src="hero.img" alt="" class="w-full h-full object-cover" />
      </div>
      <div class="flex justify-between items-center">
        <p class="text-sm font-bold px-3">{{ hero.title }}</p>
        <div class="flex flex-col items-center">
          <button class="bg-gray-100 px-2 py-1" @click="hero.quantity++">+</button>
          <span>{{ hero.quantity }}</span>
          <button class="bg-gray-100 px-2 py-1" @click="hero.quantity > 1 && hero.quantity--">-</button>
        </div>
      </div>
      <p class="text-sm text-gray-500 mt-2">{{ hero.category }}</p>
      <div class="flex items-center justify-between mt-1">
        <p class="font-semibold">{{ hero.name }}</p>
        <p class="font-semibold">${{ hero.price * hero.quantity }}</p>
      </div>
    </div>
  </div>

  <div class="bg-white p-6 shadow rounded-xl min-w-[306px] h-[347px]">
    <h2 class="text-lg font-semibold mb-4">Order Summary</h2>
    <div class="flex justify-between mb-2" v-for="(hero, index) in project" :key="'summary' + index">
      <p>{{ hero.name }} {{ hero.quantity }}</p>
      <p>${{ hero.price * hero.quantity }}</p>
    </div>
    <hr class="my-4" />
    <div class="flex justify-between font-bold">
      <p>Total<span class=" text-gray-400"></span></p>
      <p>${{ products }}</p>
    </div>

    <div class="mt-4 flex items-center gap-2">
      <input type="checkbox" id="agree" class="w-4 h-4">
      <label for="agree" class="text-sm text-[#000000]">
        I agree to the Terms & Conditions
      </label>
    </div>

    <button class="mt-4 bg-[#D9D9D9]  py-2 px-4  w-full ">
      Continue
    </button>
  </div>
</template>

<script setup>
import { ref, computed } from "vue";
import shirt from "../assets/T_shirt.png";
import shirt_two from "../assets/T_shirt_black.png";
import shirt_three from "../assets/T_shirt_black.png";

const products = computed(() =>
    project.value.reduce((total, item) => total + (item.price * item.quantity), 0)
);

const project = ref([

  {
    name: "Cotton T Shirt",
    category: "Cotton T Shirt",
    price: 99,
    title: "L",
    quantity: 1,
    img: shirt
  },
  {
    name: "Basic Slim Fit T-Shirt",
    category: "Cotton T Shirt",
    price: 99,
    title: "L",
    quantity: 1,
    img: shirt_two
  },

  {
    name: "Full Sleeve Zipper",
    category: "Cotton T Shirt",
    price: 99,
    title: "L",
    quantity: 1,
    img: shirt_three
  }

]);

</script>