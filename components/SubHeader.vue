<template>
  <div class="q-pa-md">
    <div class="row">
      <!-- Giyim menüsünün bulunduğu sütun -->
      <div 
        class="col bg-deep-purple-6" 
        style="position: relative;"
        @mouseover="openMenu"
        @mouseleave="startCloseMenu"
      >
        <q-btn flat color="white" class="full-width" ref="giyimBtn">
          Giyim
        </q-btn>
        <q-menu 
          v-model="menuVisible" 
          anchor="bottom left" 
          self="top left" 
          :style="{ width: menuWidth + 'px' }"
          @mouseover="cancelCloseMenu"
          @mouseleave="startCloseMenu"
        >
          <q-list class="wrap-menu">
            <q-item v-for="item in menuItems" :key="item.text" clickable>
              <q-item-section avatar>
                <q-img :src="item.icon" :alt="item.text" style="width: 24px; height: 24px;" />
              </q-item-section>
              <q-item-section>{{ item.text }}</q-item-section>
            </q-item>
          </q-list>
        </q-menu>
      </div>

      <!-- Diğer butonlar -->
      <div class="col bg-teal-6">
        <q-btn flat color="white" label="Çanta" class="full-width" />
      </div>
      <div class="col bg-pink-8">
        <q-btn flat color="white" label="Ayakkabı" class="full-width" @click="navigateToAyakkabi" />
      </div>
      <div class="col bg-amber-6">
        <q-btn flat color="white" label="Aksesuar" class="full-width" />
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, watch, onUnmounted } from 'vue';
import { useRouter } from 'vue-router';

const router = useRouter();
const menuVisible = ref(false);
const menuWidth = ref(0); // Menü genişliği
const giyimBtn = ref(null); // Giyim butonuna referans
let closeMenuTimeout = null;

const menuItems = [
  { text: 'Üst Giyim', icon: 'Screenshot_3073.png' },
  { text: 'Alt Giyim', icon: 'Screenshot_1.png' },
  { text: 'Elbise', icon: 'Screenshot_2.png' },
  { text: 'Dış Giyim', icon: 'Screenshot_3.png' },
  { text: 'Plaj Giyim', icon: 'Screenshot_4.png' },
  { text: 'Ev Giyim', icon: 'Screenshot_5.png' },
  { text: 'İkili Takım', icon: 'Screenshot_6.png' },
];

const navigateToAyakkabi = () => {
  router.push('/Ayakkabi');
};

const openMenu = () => {
  menuVisible.value = true;
};

const startCloseMenu = () => {
  closeMenuTimeout = setTimeout(() => {
    menuVisible.value = false;
  }, 200); // 200ms gecikme, kullanıcıyı rahatsız etmemesi için
};

const cancelCloseMenu = () => {
  clearTimeout(closeMenuTimeout);
};

// Buton genişliğini hesapla
const calculateMenuWidth = () => {
  if (giyimBtn.value) {
    menuWidth.value = giyimBtn.value.$el.getBoundingClientRect().width;
  }
};

// Menü açık/kapalı durumuna göre genişliği yeniden hesapla
watch(menuVisible, (isVisible) => {
  if (isVisible) calculateMenuWidth();
});

onMounted(() => {
  calculateMenuWidth();
  window.addEventListener('resize', calculateMenuWidth);
});

onUnmounted(() => {
  window.removeEventListener('resize', calculateMenuWidth);
});
</script>

<style>

</style>
