<template>
  <div class="container flex items-center gap-4 py-[30px]">
    <h3 class="font-medium text-[13px]">Shopping bag</h3>
    <div class="flex items-center ">
      <img :src="like_two" alt="like_two">
      <p class="font-normal text-[#8A8A8A] text-[11px]">favourites</p>
    </div>

  </div>
  <div class="flex gap-20 container">
    <div class=" grid grid-cols-2 gap-6 ">
      <div v-for="(hero, index) in project" :key="index" class="bg-white p-4 shadow rounded-xl  ">
        <div class="w-full h-64 overflow-hidden rounded-lg mb-4 flex gap-[15px]">
          <img :src="hero.img" alt="" class="w-full h-full object-cover" />
          <div class=" mt-[80px] items-center">
            <p class="text-sm font-bold px-3">{{ hero.title }}</p>
            <div class="flex flex-col items-center mt-[10px]">
              <button class="bg-gray-100 px-2 py-1" :disabled="isDisabled" @click="Increment">+</button>
              <span>{{ hero.quantity }}</span>
              <button class="bg-gray-100 px-2 py-1" @click="Decrement">-</button>
            </div>
          </div>
        </div>
        <p class="text-sm text-gray-500 mt-2">{{ hero.category }}</p>
        <div class=" flex items-center justify-between mt-1">
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
        <p>{{products}}</p>
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
  </div>

</template>

<script setup>
import { ref, computed } from "vue";
import shirt from "../assets/T_shirt.png";
import shirt_two from "../assets/T_shirt_black.png";
import shirt_three from "../assets/T_shirt_black.png";
import like_two from "../assets/like_two.svg";



const emit = defineEmits(["increment", "decrement"]);
const products = computed(() =>
    project.value.reduce((total, item) => total + (item.price * item.quantity), 0)
);
let isDisabled = ref(false);

function Increment() {
  emit("increment");
  isDisabled.value = true;
}

function Decrement() {
  emit("decrement");
  isDisabled.value = false;
}


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





<!--<template>-->
<!--  <div class="container flex items-center gap-4 py-[30px]">-->
<!--    <h3 class="font-medium text-[13px]">Shopping bag</h3>-->
<!--    <div class="flex items-center ">-->
<!--      <img :src="like_two" alt="like_two">-->
<!--      <p class="font-normal text-[#8A8A8A] text-[11px]">favourites</p>-->
<!--    </div>-->

<!--  </div>-->
<!--  <div class="flex gap-20 container">-->
<!--    <div class=" grid grid-cols-2 gap-6 ">-->
<!--      <div v-for="(hero, index) in project" :key="index" class="bg-white p-4 shadow rounded-xl  ">-->
<!--        <div class="w-full h-64 overflow-hidden rounded-lg mb-4 flex gap-[15px]">-->
<!--          <img :src="hero.img" alt="" class="w-full h-full object-cover" />-->
<!--          <div class=" mt-[80px] items-center">-->
<!--            <p class="text-sm font-bold px-3">{{ hero.title }}</p>-->
<!--            <div class="flex flex-col items-center mt-[10px]">-->
<!--              <button class="bg-gray-100 px-2 py-1" @click="Increment(index)">+</button>-->
<!--              <span>{{ hero.quantity }}</span>-->
<!--              <button class="bg-gray-100 px-2 py-1" @click="Decrement(index)">-</button>-->
<!--            </div>-->
<!--          </div>-->
<!--        </div>-->
<!--        <p class="text-sm text-gray-500 mt-2">{{ hero.category }}</p>-->
<!--        <div class=" flex items-center justify-between mt-1">-->
<!--          <p class="font-semibold">{{ hero.name }}</p>-->
<!--          <p class="font-semibold">${{ hero.price * hero.quantity }}</p>-->
<!--        </div>-->
<!--      </div>-->
<!--    </div>-->

<!--    <div class="bg-white p-6 shadow rounded-xl min-w-[306px] h-[347px]">-->
<!--      <h2 class="text-lg font-semibold mb-4">Order Summary</h2>-->
<!--      <div class="flex justify-between mb-2" v-for="(hero, index) in project" :key="'summary' + index">-->
<!--        <p>{{ hero.name }} {{ hero.quantity }}</p>-->
<!--        <p>${{ hero.price * hero.quantity }}</p>-->
<!--      </div>-->
<!--      <hr class="my-4" />-->
<!--      <div class="flex justify-between font-bold">-->
<!--        <p>Total</p>-->
<!--        <p>${{ totalPrice }}</p>-->
<!--      </div>-->

<!--      <div class="mt-4 flex items-center gap-2">-->
<!--        <input type="checkbox" id="agree" class="w-4 h-4">-->
<!--        <label for="agree" class="text-sm text-[#000000]">-->
<!--          I agree to the Terms & Conditions-->
<!--        </label>-->
<!--      </div>-->
<!--      <button class="mt-4 bg-[#D9D9D9]  py-2 px-4  w-full ">-->
<!--        Continue-->
<!--      </button>-->
<!--    </div>-->
<!--  </div>-->

<!--</template>-->

<!--<script setup>-->
<!--import { ref, computed } from "vue";-->
<!--import shirt from "../assets/T_shirt.png";-->
<!--import shirt_two from "../assets/T_shirt_black.png";-->
<!--import shirt_three from "../assets/T_shirt_black.png";-->
<!--import like_two from "../assets/like_two.svg";-->

<!--const emit = defineEmits(["increment", "decrement"]);-->

<!--const totalPrice = computed(() =>-->
<!--    project.value.reduce((total, item) => total + (item.price * item.quantity), 0)-->
<!--);-->

<!--function Increment(index) {-->
<!--  project.value[index].quantity++;-->
<!--  emit("increment", { index, product: project.value[index] });-->
<!--}-->

<!--function Decrement(index) {-->
<!--  if (project.value[index].quantity > 1) {-->
<!--    project.value[index].quantity&#45;&#45;;-->
<!--    emit("decrement", { index, product: project.value[index] });-->
<!--  }-->
<!--}-->

<!--const project = ref([-->

<!--  {-->
<!--    name: "Cotton T Shirt",-->
<!--    category: "Cotton T Shirt",-->
<!--    price: 99,-->
<!--    title: "L",-->
<!--    quantity: 1,-->
<!--    img: shirt-->
<!--  },-->
<!--  {-->
<!--    name: "Basic Slim Fit T-Shirt",-->
<!--    category: "Cotton T Shirt",-->
<!--    price: 99,-->
<!--    title: "L",-->
<!--    quantity: 1,-->
<!--    img: shirt_two-->
<!--  },-->

<!--  {-->
<!--    name: "Full Sleeve Zipper",-->
<!--    category: "Cotton T Shirt",-->
<!--    price: 99,-->
<!--    title: "L",-->
<!--    quantity: 1,-->
<!--    img: shirt_three-->
<!--  }-->

<!--]);-->

<!--</script>-->