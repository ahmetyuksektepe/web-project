<template>
    <div class="row justify-center q-gutter-sm">
            <q-intersection
              v-for="item in items2"
              :key="item.id"
              class="card-item"
              style="margin-bottom: 60px; height: 290px; width: 290px"
            >
              <q-card class="my-card" flat bordered>
                <q-card-section>
                  <div
                    class="text-h10 q-mb-xs"
                    style="overflow: hidden; text-overflow: ellipsis; white-space: nowrap;"
                  >
                    <q-avatar size="31px">
                      <img :src="item.avatar" />
                    </q-avatar>
                    {{ item.satici }}
                    <q-btn
                      outline
                      color="red-5"
                      icon="add"
                      size="8px"
                      label="Takip Et"
                    />
                  </div>
                  <div class="row no-wrap items-center">
                    <q-rating
                      v-model="ratingModel"
                      size="1.5em"
                      color="green-5"
                      icon="star_border"
                      icon-selected="star"
                    />
                    <span class="text-caption text-grey q-ml-sm">{{ item.rate }}</span>
                  </div>
                </q-card-section>
                <q-img :src="item.source" width="262px" height="147px" />
                <q-card-actions>
                  <div class="q-pa-md example-row-equal-width">
                    <div class="row">
                      <div class="col justify-start text-h7">{{ item.info }}</div>
                      <div class="col absolute-bottom-right text-h5">
                        {{ item.fiyat }} TL
                      </div>
                    </div>
                  </div>
                </q-card-actions>
                <q-card-actions>
                  <q-btn size="8px" unelevated unrounded color="cyan" icon="add" />
                </q-card-actions>
              </q-card>
            </q-intersection>
          </div>
  </template>
  
  <script setup>
  import { ref } from "vue";
  
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
  </script>
  