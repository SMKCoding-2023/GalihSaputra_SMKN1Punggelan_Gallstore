<script lang="ts" setup>
import { useProductsStore } from "~/stores/products";


const productStore = useProductsStore();
const allProducts = ref([]);

productStore.getAllProducts().then(() => {
allProducts.value = productStore.products;
});

const selectedCategory = ref("");
</script>


<template>
   <div class="bg-gray-400">
    <section>
      <div class="container">
        <div class="py-10">
          <div class="mb-6 flex justify-end gap-6, ndas">
            <h1 style="padding: auto; margin: auto">produk</h1>
            <Dropdown @selected-category="selectedCategory = $event" />
          </div>
          <div class="flex gap-3 flex-wrap mx-2 ">
            <template v-for="(item, index) in allProducts" :key="index">
              <CardsCardProduct :product="item" class="w-1/1 h-1/1" />
            </template>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>
