<template>
    <q-page>
      <Header />
  
      <SubHeader />
  
      <div class="q-col">
        <div class="kategori" style="width: 40em">
          <div class="q-pa-md" style="width: 26em">
            <!-- Kategori Listesi -->
            <Categories />
  
            <!-- Fiyat Filtreleri -->
            <Price />
          </div>
        </div>
  
        <!-- Ürünler -->
        <div>
          <div class="text-h6" style="position: relative; left: 55px">
            Spor Ayakkabı <b>9.578 ürün</b>
          </div>
            <ProductCard2 />
        </div>
      </div>
    </q-page>
  </template>
  
  <script>
  import { ref } from "vue";
import Header from "~/components/Header.vue";
  
  export default {
    setup() {
      const arama = ref("");
      const ratingModel = ref(4);
      const items2 = ref([]);
  
      // Rastgele Ürün Verisi Yükleme
      const loadItems = () => {
        items2.value = Array.from({ length: 15 }, (_, index) => ({
          id: index + 1,
          avatar: `/Screenshot_${3061 + (index % 12)}.png`,
          satici: `Satıcı ${index + 1}`,
          rate: (Math.random() * 5).toFixed(1),
          source: `/Screenshot_${3024 + (index % 37)}.png`,
          info: `Ürün ${index + 1}`,
          fiyat: (Math.random() * 500).toFixed(2),
        }));
      };
  
      loadItems();
  
      return { arama, ratingModel, items2 };
    },
  };
  </script>
  