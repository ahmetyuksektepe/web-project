<template>
    <div class="q-mt-none">
        <div class="row items-center justify-center q-gutter-md">
          <q-img
            src="https://cdn.dolap.com/web/images/logo-5.svg"
            style="max-width: 140px; height: 68px"
          />
  
          <div class="col-5">
            <q-input
              v-model="arama"
              filled
              type="search"
              placeholder="Ürün, @üye, #etiket ara"
              class="col-5"
            >
              <template v-slot:append>
                <q-icon name="search" />
              </template>
            </q-input>
          </div>
          <div class="row items-center">
            <q-btn flat color="black" label="Markalar" />
            <q-btn flat color="black" label="Giriş Yap" />
          </div>
        </div>
      </div>
</template>

<script setup lang="ts">    
      const arama = ref("");
</script>