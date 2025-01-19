<template>
  <q-page>
    <Header />
    <SubHeader />

    <div style="display: flex; align-items: flex-start; justify-content: space-between; padding: 10px;">
      <!-- Görsel -->
      <q-img
        src="https://cdn.dolap.com/web/images/telephone_login.png"
        style="width: 332px; height: 487px; margin-right: 20px; margin-left: 400px;"
      >
      </q-img>

      <!-- Giriş Formu ve Carousel -->
      <div
        class="column no-wrap justify-center items-center content-center"
        style="
          width: 20vw;
          overflow: auto;
          border: 0.5px solid rgba(0, 0, 0, 0.3);
          margin: 0 auto;
          border-radius: 1px;
          padding: 0em;

        "
      >
        <!-- Carousel -->
        <div
          class="text-h5 text-weight-bold"
          style="text-align: center; margin: 1em"
        >
          DOLAP'A GİRİŞ YAP
        </div>
        <!-- Giriş Formu -->
        <Login />
      </div>
    </div>

    <Footer />
  </q-page>
</template>

<script setup lang="ts">
</script>
