<template>
    <q-drawer v-model="drawer" side="right" width="400px" bordered>
      <!-- Header -->
      <div class="flex items-center justify-between p-4 border-b">
        <h2 class="text-lg font-bold text-purple-700 flex items-center space-x-2">
          <span class="text-orange-500 text-xl">🛒</span>
          <span>Sepetim</span>
        </h2>
      </div>
  
      <!-- Cart Items -->
      <div class="flex-1 overflow-y-auto p-4">
        <div v-for="item in cartStore.items" :key="item.id" class="cart-item rounded-lg shadow-md p-4 border">
          <q-img :src="item.source" alt="Ürün Resmi" class="book-image mr-4" />
          <div class="cart-item-content">
            <p class="text-sm font-semibold"> Ürün: {{ item.info }}</p>
            <p class="text-lg font-bold text-purple-600">Fiyat: {{ item.fiyat }} TL</p>
            <p class="text-lg font-bold text-purple-600">Satıcı: {{ item.satici }} TL</p>
            <div class="flex items-center mt-2">
              <q-btn flat icon="remove" @click="cartStore.decreaseQuantity(item)" />
              <span class="q-mx-md">{{ item.quantity }}</span>
              <q-btn flat icon="add" @click="cartStore.increaseQuantity(item)" />
            </div>
          </div>
        </div>
      </div>
  
      <!-- Summary -->
      <div class="p-4 border-t">
        <div class="flex justify-between mb-2">
          <span>Sepet Toplamı</span>
          <span class="font-bold">{{ cartStore.cartTotal.toFixed(2) }} TL</span>
        </div>
        <div class="flex justify-between mb-2">
          <span>Kargo Ücreti</span>
          <span class="font-bold">{{ cartStore.shippingFee.toFixed(2) }} TL</span>
        </div>
        <div class="flex justify-between mb-4">
          <span>Genel Toplam</span>
          <span class="font-bold text-purple-700">{{ cartStore.grandTotal.toFixed(2) }} TL</span>
        </div>
        <q-btn color="primary" unelevated label="Satın Al" class="full-width" @click="checkout" />
      </div>
    </q-drawer>
  </template>
  
  <script setup lang="ts">
  import { ref } from 'vue';
  import { useCartStore } from '@/stores/cart';
  import { useQuasar } from 'quasar';
  
  const cartStore = useCartStore();
  const $q = useQuasar(); // Quasar Notify için
  
  // Çekmeceyi kapatma işlevi

  
  // Satın alma işlevi
  const checkout = () => {
    if (cartStore.items.length === 0) {
      $q.notify({
        type: 'negative',
        message: 'Sepetiniz boş. Lütfen ürün ekleyin.',
        position: 'top-right',
      });
      return;
    }
  
    cartStore.clearCart(); // Sepeti temizle
  
    $q.notify({
      type: 'positive',
      message: 'Siparişiniz başarıyla alındı!',
      position: 'top-right',
    });
  };
  </script>
  
  <style scoped>
  
  </style>
  