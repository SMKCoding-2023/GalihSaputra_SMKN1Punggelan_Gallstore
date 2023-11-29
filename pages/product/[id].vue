<script lang="ts" setup>
import { useProductsStore } from "~/stores/products";

const product = useProductsStore();
const allProducts = ref([]);

product.getAllProducts().then(() => {
allProducts.value = product.products;
});

const selectedCategory = ref("");
</script>

definePageMeta({
  middleware: ["user-access"]
 });


<!-- <script lang="ts" setup>
import { products } from "~/composables/constants/products";
import { Products } from "~/types/products";
const route = useRoute();
const id =
  typeof route.params.id === "string" ? parseInt(route.params.id) : null;
const product = ref(products.find((item: Products) => item.id === id));
</script> -->
<template>
  <DetailProduct :product="product" />
</template>
