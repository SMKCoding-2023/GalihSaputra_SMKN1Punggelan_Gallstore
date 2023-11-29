<script lang="ts" setup>
import { useProductsStore } from "~/stores/products";

const productStore = useProductsStore();
const allProducts = ref([]);

productStore.getAllProducts().then(() => {
allProducts.value = productStore.products;
});

const selectedCategory = ref("");
</script>

definePageMeta({
  middleware: ["user-access"]
 });

<template>
   <div class="bg-gray-400">
    <section>
      <div class="container">
        <div class="py-10">
          <div class="mb-6 flex justify-end gap-6, ndas">
            <h1 style="padding: auto; margin: auto">produk</h1>
            <Dropdown @selected-category="selectedCategory = $event" />
            <NuxtLink
              to="/category/create"
              class="bg-orange-500 text-white flex justify- center items-center px-3 rounded-lg"
              >Create Category</NuxtLink>

              <NuxtLink to="/product/create" class="bg-green-500 text-white flex justify-center
items-center px-3 rounded-lg">Create Products</NuxtLink>
          </div>
          <div class="flex gap-6 flex-wrap mx-auto">
            <template v-for="(item, index) in allProducts" :key="index">
              <CardsCardProduct :product="item" class="w-1/1" />
            </template>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>
