<template>
  <header class="container">
    <div class="mt-[62px]">
      <div v-for="(product,index) in products" :key="index" >
        <div class=" flex justify-between">
          <div class="flex gap-[36px] items-center">
            <img :src="product.img" alt="hr_three">
            <div class="flex gap-[32px]">
              <p class="font-medium	text-[16px]">{{ product.home }}</p>
              <p class="font-medium	text-[16px]">{{ product.name }}</p>
              <p class="font-medium	text-[16px]">{{ product.new }}</p>
            </div>

          </div>
          <div class="flex gap-[45px]">
            <img :src="product.images" alt="">
            <div class="flex ">
              <div class="bg-[#000000] py-[15px] text-[12px] px-[20px] max-w-[76px] max-h-[50px] rounded-[22px] text-white">Cart</div>
              <img :src="basket" class="ml-[-5px]" alt="basket">
            </div>
            <img :src="people" alt="people_img">

          </div>
        </div>

      </div>
    </div>
  </header>
</template>

<script setup>
import {ref} from "vue";
import hr_three from "../../assets/hr_three.svg";
import like from "../../assets/like.svg";
import basket from "../../assets/basket.svg";
import people from "../../assets/people.svg";

const products = ref(
    [
      {
        img:hr_three,
        home: "Home",
        name: "Collections",
        new:"New",
        images:like,
      },

    ])
</script>