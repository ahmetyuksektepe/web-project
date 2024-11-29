<template>
    <q-layout view="hHh lpR fFf">
      
      <q-header elevated class="bg-green text-white" height-hint="98">
        <q-toolbar>
          <q-toolbar-title>
            Ahmet Faruk Yüksektepe 210101038  -   Muhammed Eren ŞANCI 210101017
          </q-toolbar-title>
        </q-toolbar>
  
        
        <q-tabs align="left">
          <q-route-tab to="/" label="Anasayfa" />
          <q-route-tab to="/Ayakkabi" label="Ayakkabı ilan sayfası" />
          <q-route-tab to="/Kaydol" label="Üye ol sayfası" />
        </q-tabs>
      </q-header>
  
      
      <q-page-container>
        <NuxtPage />
      </q-page-container>
    </q-layout>
  </template>
  
  <script setup lang="ts">
  import { useQuasar } from "quasar";
  
  const $q = useQuasar(); // Quasar'ın özelliklerine erişim
  </script>
  
  