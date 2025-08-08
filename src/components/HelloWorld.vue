<template>
  <div class="max-w-6xl mx-auto p-8">
    <h1 class="text-3xl font-bold text-center mb-8 text-gray-800"> Mahsulotlar Ro'yxati</h1>

    <form @submit.prevent="Submit" class="bg-white p-6 rounded-xl shadow mb-10 grid grid-cols-1 md:grid-cols-2 gap-4">
      <input v-model="form.img" placeholder="Rasm URL" class="border rounded-lg px-4 py-2 focus:outline-none focus:ring-2 focus:ring-blue-400" />
      <input v-model="form.price" placeholder="narxi" class="border rounded-lg px-4 py-2 focus:outline-none focus:ring-2 focus:ring-blue-400" />
      <input v-model="form.year" placeholder="Yili" class="border rounded-lg px-4 py-2 focus:outline-none focus:ring-2 focus:ring-blue-400" />

      <button
          @click="updateBtn"
          class="bg-blue-600 text-white px-6 py-2 rounded-lg hover:bg-blue-700 transition duration-300"
      >
        sent
      </button>
    </form>

    <div class="grid sm:grid-cols-2 lg:grid-cols-3 gap-6">
      <div
          v-for="(pro, index) in products"
          :key="index"
          class="bg-white rounded-xl shadow hover:shadow-lg transition overflow-hidden"
      >
        <img :src="pro.img" alt="Car" class="w-full h-48 object-cover" />
        <div class="p-4 space-y-1">
          <h2 class="text-lg font-bold text-gray-800"> {{ pro.price }}</h2>
          <p class="text-sm text-gray-600">Yil: {{ pro.year }}</p>

          <div class="flex justify-between mt-4">
            <button @click="editUser(index)" class="bg-yellow-400 text-white px-3 py-1 rounded-md hover:bg-yellow-500">Tahrirlash</button>
            <button @click="deleteUser(index)" class="bg-red-500 text-white px-3 py-1 rounded-md hover:bg-red-600">O'chirish</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, reactive  } from 'vue';

const products = ref([]);
const form = reactive({
  price: '',
  img: '',
  year: '',
});
const editIndex = ref(null);

const Submit = () => {
  const newItem = { ...form };

  if (editIndex.value !== null) {
    products.value[editIndex.value] = newItem;
    editIndex.value = null;
  } else {
    products.value.push(newItem);
  }

  Object.keys(form).forEach((key) => (form[key] = ''));
};

const editUser = (index) => {
  const item = products.value[index];
  Object.keys(form).forEach((key) => (form[key] = item[key]));
  editIndex.value = index;
};

const deleteUser = (index) => {

  products.value.splice(index, 1);

  if (editIndex.value === index) {

    editIndex.value = null;

    Object.keys(form).forEach((key) => (form[key] = ''));
  }
};
</script>
