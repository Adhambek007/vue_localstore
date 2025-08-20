<template>
  <section class="bg-black text-white py-12 px-6">
    <h2 class="text-3xl font-bold text-center mb-8">
      Bajargan loyihalarimiz
    </h2>

    <div class="flex justify-center mb-10">
      <div class="inline-flex items-center bg-[#1A1A1A] rounded-full p-1 space-x-1">
        <button
            v-for="tab in tabs"
            :key="tab.value"
            @click="activeTab = tab.value"
            class="px-4 py-2 text-sm font-medium rounded-full transition-all duration-300"
            :class="{
            'bg-gradient-to-r from-purple-600 to-indigo-600 text-white': activeTab === tab.value,
            'text-white hover:text-purple-400': activeTab !== tab.value }">
          {{ tab.label }}
        </button>
      </div>
    </div>
    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
      <div v-for="(product, index) in filteredProducts" :key="index" class="relative w-full h-[362px] rounded-xl overflow-hidden border border-gray-800 bg-black">
        <div class="absolute inset-2 bg-gradient-to-t from-black  z-10"></div>
        <img :src="product.img" alt="product " class="w-full h-full object-cover opacity-40"/>
        <div class="absolute top-3 right-3 bg-white text-black text-xs px-3 py-1 rounded-full font-medium z-20">
          {{ product.new }}
        </div>
        <div class="absolute top-3 right-0 pr-1 pt-1 z-20">
          <img :src="product.images" alt="images" class="w-[60px] h-[60px] opacity-80" />
        </div>
        <div class="absolute bottom-4 left-4 text-white text-lg font-semibold w-[85%] z-20">
          {{ product.name }}
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed } from 'vue'
import cursore from '../../assets/cursore.svg'
import iphone_pro from '../../assets/iphone_pro.png'

const tabs = [
  {
    label: 'Barchasi',
    value: 'all'
  },
  {
    label: 'Veb sayt',
    value: 'Veb sayt'
  },
  {
    label: 'Veb dizayn',
    value: 'Veb dizayn'
  },
  {
    label: 'SMM',
    value: 'SMM'
  },
  {
    label: 'Mobil ilova',
    value: 'Mobil ilova'
  },
]

const activeTab = ref('all')

const products = ref([
  {
    img: iphone_pro,
    name: 'UYMAKON mobil ilovasi',
    new: 'Mobil ilova',
    images: cursore,
  },
  {
    img: iphone_pro,
    name: 'AvtoWeb Landing',
    new: 'Veb sayt',
    images: cursore,
  },
  {
    img: iphone_pro,
    name: 'Dizayn Studio',
    new: 'Veb dizayn',
    images: cursore,
  },
  {
    img: iphone_pro,
    name: 'SMM Strategiyasi',
    new: 'SMM',
    images: cursore,
  },
  {
    img: iphone_pro,
    name: 'Bolalar o"yin dasturi',
    new: 'Mobil ilova',
    images: cursore,
  },
  {
    img: iphone_pro,
    name: 'Portfolio sayti',
    new: 'Veb sayt',
    images: cursore,
  },
  {
    img: iphone_pro,
    name: 'Portfolio sayti',
    new: 'Veb sayt',
    images: cursore,
  },
  {
    img: iphone_pro,
    name: 'Bolalar o"yin dasturi',
    new: 'Mobil ilova',
    images: cursore,
  },
  {
    img: iphone_pro,
    name: 'SMM Strategiyasi',
    new: 'SMM',
    images: cursore,
  },
])

const filteredProducts = computed(() => {
  if (activeTab.value === 'all') return products.value
  return products.value.filter(product => product.new === activeTab.value)
})
</script>