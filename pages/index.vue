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
  
  <div>
    <!-- Hero Section -->
    <section class="bg-gray-800 from-purple-700 to-indigo-500 py-16 text-center text-white">
      <div class="container mx-auto">
        <h1 class="text-4xl font-bold mb-4 animate__animated animate__fadeIn">Selamat Datang di Gallstore</h1>
        <p class="text-lg mb-8 animate__animated animate__fadeInUp">Temukan produk terbaik untuk kebutuhan Anda.</p>
        <router-link to="/product" class="text-white animate__animated animate__fadeIn">
          <button class="bg-blue-500 hover:bg-blue-600 text-white px-6 py-3 rounded transition-all duration-300 transform hover:scale-105">
            Lihat Produk
          </button>
        </router-link>
      </div>
    </section>

    <!-- Featured Products Section -->
    <div class="bg-gray-400">
    <section>
      <div class="container">
        <div class="py-10">
          <div class="flex gap-3 flex-wrap mx-auto">
            <template v-for="(item, index) in allProducts" :key="index">
              <CardsCardProduct :product="item" class="w-1/4 h-1/5" />
            </template>
          </div>
        </div>
      </div>
    </section>
  </div>
    <!-- Testimonials Section -->
    <section class="py-16 bg-gradient-to-r from-indigo-500 to-blue-500 text-white">
      <div class="container mx-auto text-center">
        <h2 class="text-3xl font-bold mb-8 animate__animated animate__fadeIn">Apa Kata Mereka?</h2>
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          <!-- Testimonial 1 -->
          <div class="p-6 bg-white rounded-lg shadow-md hover:shadow-xl transition-all duration-300 transform hover:scale-105">
            <p class="text-gray-700 mb-4">"Pelayanan luar biasa, produk berkualitas tinggi!"</p>
            <p class="font-semibold">- Pelanggan 1</p>
          </div>

          <!-- Testimonial 2 -->
          <div class="p-6 bg-white rounded-lg shadow-md hover:shadow-xl transition-all duration-300 transform hover:scale-105">
            <p class="text-gray-700 mb-4">"Sangat puas dengan pembelian saya, akan kembali lagi!"</p>
            <p class="font-semibold">- Pelanggan 2</p>
          </div>

          <!-- Testimonial 3 -->
          <div class="p-6 bg-white rounded-lg shadow-md hover:shadow-xl transition-all duration-300 transform hover:scale-105">
            <p class="text-gray-700 mb-4">"Produk sesuai dengan ekspektasi, terima kasih!"</p>
            <p class="font-semibold">- Pelanggan 3</p>
          </div>
        </div>
      </div>
    </section>
  </div>

</template>

<!-- <script>
export default {
  name: 'Home',
};
</script> -->

<style scoped>
.container {
  max-width: 1200px;
  margin: 0 auto;
}
</style>
