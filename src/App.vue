<template>
  <div class="flex justify-center items-center border-2 min-h-screen">
    <div class="w-3/4 p-3 shadow-xl">
      <h1 class="text-3xl font-semibold mb-5 text-center underline">
        List of Products
      </h1>
      <div class="mt-4 flex gap-2">
        <label class="font-semibold">Search Products: </label>
        <input
          v-model="searchItem"
          type="text"
          class="border-[1px] border-solid bg-transparent rounded-sm focus:outline-none px-2 text-sm"
        />
      </div>
      <div>
        <ul class="grid grid-cols-2 gap-5">
          <li
            class="shadow px-3 py-4"
            v-for="(item, index) in filteredItemBySearch"
            :key="index"
          >
            <p>Name: {{ item.title }}</p>
            <p>Price: ${{ item.price }}</p>
            <p>Quantity: {{ item.quantity }}</p>
            <p>{{ availability }}</p>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script setup>
import { computed, ref } from "vue";

const searchItem = ref("");
const items = [
  {
    title: "iPhone 9",
    price: 549,
    quantity: 0,
  },
  {
    title: "iPhone X",
    price: 899,
    quantity: 10,
  },
  {
    title: "Samsung Universe 9",
    price: 1249,
    quantity: 20,
  },
  {
    title: "OPPOF19",
    price: 280,
    quantity: 30,
  },
  {
    title: "Huawei P30",
    price: 499,
    quantity: 30,
  },
  {
    title: "MacBook Pro",
    price: 1749,
    quantity: 30,
  },
  {
    title: "Microsoft Surface Laptop 4",
    price: 1499,
    quantity: 30,
  },
  {
    title: "Infinix INBOOK",
    price: 1099,
    quantity: 30,
  },
];

const filteredItemBySearch = computed(() => {
  return items.filter((item) =>
    item.title
      .toLocaleLowerCase()
      .includes(searchItem.value.toLocaleLowerCase())
  );
});
const filteredItem = filteredItemBySearch;
</script>