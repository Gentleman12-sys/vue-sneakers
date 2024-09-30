<script setup>
import Header from './components/Header.vue'
import ProductList from './components/ProductList.vue'
import Drawer from './components/Drawer.vue'
import { onMounted, ref, watch } from 'vue';
import axios from 'axios';

const items = ref([]);
const sortBy = ref('');
const searchQuery = ref('');
const drawerOpen = ref(false);

const toggleDrawer = (val) => {
  drawerOpen.value = val;
}

const onChangeSelect = event => {
  sortBy.value = event.target.value;
}

const fetchItems = async () => {
  try {
    const { data } = await axios.get(`https://ccbe1b73bcd87a9f.mokky.dev/items?sortBy=${sortBy.value}&title=*${searchQuery.value}*`); 
    items.value = data;
  } catch (error) {
    console.log(error);
  }
}

onMounted(fetchItems);

watch(sortBy, fetchItems);
watch(searchQuery, fetchItems);
</script>

<template>
  <div>
    <Drawer
    v-if="drawerOpen"
    @toggleDrawer="toggleDrawer"
    />
    <div class="bg-white w-4/5 m-auto h-fit rounded-xl shadow-xl mt-5 p-2 mb-5">
      <Header @toggleDrawer="toggleDrawer" />
      <div class="p-10">
        <div class="justify-between flex">
          <h2 class="text-3xl font-bold mb-8">Все кросовки</h2>

          <div class="flex gap-4">
            <select @change="onChangeSelect" class="h-min py-2 px-3 border rounded-md outline-none">
              <option value="title">По названию</option>
              <option value="price">Сначала дешевле</option>
              <option value="-price">Сначала дороже</option>
            </select>
            <div class="relative">
              <input
              class="border rounded-md py-2 pl-2 pr-2 outline-none focus:border-gray-400"
              type="text"
              placeholder="Поиск..."
              v-model="searchQuery">
            </div>
          </div>
        </div>
        <ProductList :items="items" />
      </div>
    </div>
  </div>
</template>