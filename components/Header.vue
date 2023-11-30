<script lang="ts" setup>
import { useAuthStore } from "~/stores/auth"
const authStore = useAuthStore();
const isAuthenticated = ref();
const router = useRouter();
isAuthenticated.value = useCookie("access_token").value;
const logout = async () => {
 await authStore.logout();
 const accessToken = useCookie("access_token");
 const refreshToken = useCookie("refresh_token");
 accessToken.value = null;
 refreshToken.value = null;
 setTimeout(() => {
 isAuthenticated.value = useCookie("access_token").value;
 }, 100);
 router.push({
 path: "/"
 })
}
</script>

<template>
  <header class="bg-gray-800 p-4 flex justify-between items-center text-white">
    <div class="container">
      <div class="flex justify-between items-center">
        <div>
          <NuxtLink to="/" class="text-xl font-bold">Gallstore</NuxtLink>
        </div>
        <nav class="flex items-center gap-6">
          <NuxtLink to="/" class="text-base">🏠</NuxtLink>

          <NuxtLink to="/product" class="text-base">🛍️</NuxtLink>
 <NuxtLink to="/cart" class="text-base"> 🛒</NuxtLink>
          <NuxtLink
              to="/category/create"
              class="bg-orange-500 text-white flex justify- center items-center px-3 rounded-lg"
              >type</NuxtLink>
 
              <NuxtLink to="/product/create" class="bg-green-500 text-white flex justify-center
items-center px-3 rounded-lg">jual</NuxtLink>
         
          <NuxtLink v-if="!isAuthenticated" to="/login" class="text-base bg-blue-600
px-6 py-2 text-white rounded-lg hover:bg-blue-600/80">Login</NuxtLink>
<div v-else class="text-base cursor-pointer bg-red-600 px-6 py-2 text-white
rounded-lg hover:bg-red-600/80" @click="logout">Logout</div>
        </nav>
      </div>
    </div>
  </header>
</template>
