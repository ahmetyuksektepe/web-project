<template>
    <q-form @submit="onSubmit" @reset="resetForm" class="q-gutter-md">
      <q-input
        filled
        v-model="name"
        label="Adınız ve Soyadınız *"
        lazy-rules
        :rules="[val => !!val || 'Lütfen bir şey giriniz']"
      />
      <q-input
        filled
        type="number"
        v-model="age"
        label="Yaşınız *"
        lazy-rules
        :rules="[val => !!val || 'Yaşınızı yazınız', val => (val > 0 && val < 100) || 'Geçerli bir yaş giriniz']"
      />
      <q-input
        v-model="email"
        filled
        type="email"
        label="Email *"
        lazy-rules
        :rules="[val => !!val || 'Bir email giriniz!']"
      />
      <q-input
        filled
        v-model="phone"
        label="Telefon *"
        mask="(###) ### - ####"
        lazy-rules
        :rules="[val => !!val || 'Bir numara giriniz']"
      />
      <q-input
        v-model="password"
        filled
        :type="isPwd ? 'password' : 'text'"
        label="Şifre *"
        lazy-rules
        :rules="[val => !!val || 'Bir şifre giriniz']"
      >
        <template v-slot:append>
          <q-icon
            :name="isPwd ? 'visibility_off' : 'visibility'"
            class="cursor-pointer"
            @click="isPwd = !isPwd"
          />
        </template>
      </q-input>
  
      <q-toggle
        v-model="accept"
        label="Kullanım lisans ve koşullarını kabul ediyorum"
      />
      <q-separator />
  
      <div>
        <q-btn label="Kaydol" type="submit" color="teal-5" @click="addUye" />
        <q-btn
          size="15px"
          elevated
          rounded
          color="teal-5"
          label="Üyelikleri Görüntüle"
          @click="toggleDialog"
        />
        <q-dialog v-model="icon">
          <q-card>
            <q-card-section class="row items-center q-pb-none">
              <div class="text-h6">Üyelikler</div>
              <q-space />
              <q-btn
                icon="delete"
                flat
                round
                color="teal-5"
                label="Tümünü Sil"
                @click="deleteUyeler"
              />
              <q-btn
                flat
                round
                color="teal-5"
                label="Yenile"
                @click="loadUyeler"
              />
              <q-btn icon="close" flat round dense v-close-popup />
            </q-card-section>
            <div class="q-pa-md flex justify-center">
              <div style="max-width: 90%; width: 300px">
                <q-item v-for="item in uyeler" :key="item.id" clickable v-ripple>
                  <q-item-section>
                    <q-item-label>İsim: {{ item.name }}</q-item-label>
                    <q-item-label caption lines="1">Email: {{ item.email }}</q-item-label>
                    <q-item-label caption lines="1">Yaş: {{ item.age }}</q-item-label>
                  </q-item-section>
                </q-item>
              </div>
            </div>
          </q-card>
        </q-dialog>
      </div>
    </q-form>
  </template>
  
  <script setup>
  import { ref } from "vue";
  
  const uyeler = ref([]);
  const icon = ref(false);
  const name = ref("");
  const age = ref(null);
  const email = ref("");
  const phone = ref("");
  const password = ref("");
  const isPwd = ref(true);
  const accept = ref(false);
  
  const toggleDialog = () => {
    icon.value = !icon.value;
  };
  
  const addUye = () => {
    uyeler.value.push({
      id: uyeler.value.length + 1,
      name: name.value,
      age: age.value,
      email: email.value,
    });
    resetForm();
  };
  
  const resetForm = () => {
    name.value = "";
    age.value = null;
    email.value = "";
    phone.value = "";
    password.value = "";
    accept.value = false;
  };
  
  const deleteUyeler = () => {
    uyeler.value = [];
  };
  </script>
  