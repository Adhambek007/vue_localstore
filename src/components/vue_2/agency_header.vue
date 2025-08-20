<template>
  <header class="bg-[#121212] text-white py-4 px-8 flex justify-between items-center">
    <div class="text-[30px] font-medium">Logo</div>
    <nav class="flex gap-6 text-sm">
      <a href="#" class="hover:text-purple-400">О компании</a>
      <a href="#" class="hover:text-purple-400">Портфолио</a>
      <a href="#" class="hover:text-purple-400">Услуги</a>
      <a href="#" class="hover:text-purple-400">Контакты</a>
    </nav>

    <div class="flex items-center gap-4">
      <img :src="night" alt="" >
      <div class="text-sm font-medium ">
       <p>+998 90 777-77-77</p>
        <p>chatbotamir@gmail.com</p>

      </div>

      <div class="text-sm font-medium ">
      </div>
      <button class="bg-purple-600 hover:bg-purple-700 text-white text-sm px-4 py-2 rounded-md">
        Заказать звонок
      </button>
    </div>
  </header>
</template>

<script setup>
import night from "../../assets/night.svg"
</script>



