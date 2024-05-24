<template>
  <q-layout view="hHh lpR fFf">

    <q-header elevated class="bg-purple text-white" height-hint="98">
      <q-toolbar class="justify-end">
        <q-btn dense flat round icon="menu" @click="toggleLeftDrawer" />

        <q-toolbar-title>
          <q-icon name="shopping_cart" class="text-white" />
          Toko Online
        </q-toolbar-title>

        <q-tabs align="right">
          <q-btn flat round color="text-white" icon="search" size="15px"/>
          <q-btn flat round color="text-white" icon="notifications" size="15px"/>
          <q-btn flat round color="text-white" icon="shopping_cart" size="15px"/>
        </q-tabs>

        <q-btn round>
          <q-avatar size="35px">
            <img src="https://cdn.quasar.dev/img/avatar2.jpg" />
          </q-avatar>
        </q-btn>
      </q-toolbar>
    </q-header>

    <q-drawer show-if-above v-model="leftDrawerOpen" side="left" bordered>
      <q-scroll-area class="fit">
        <q-list padding class="menu-list">
          <q-item active clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="inbox" />
            </q-item-section>
            <q-item-section>Beranda</q-item-section>
          </q-item>

          <q-item clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="new_releases" />
            </q-item-section>
            <q-item-section>Promo Baru</q-item-section>
          </q-item>

          <q-item clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="send" />
            </q-item-section>
            <q-item-section>Send</q-item-section>
          </q-item>

          <q-item clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="drafts" />
            </q-item-section>
            <q-item-section>Chat</q-item-section>
          </q-item>
        </q-list>
      </q-scroll-area>
    </q-drawer>

    <q-page-container>
      <router-view />

      <!-- Carousel Gambar -->
      <div class="carousel-container q-pa-md">
        <q-carousel v-model="slide" arrows infinite animated-transition>
          <q-carousel-slide
            v-for="(image, index) in images"
            :key="index"
            :name="image.name"
            :img-src="image.src"
          />
          <q-carousel-control position="bottom-right">
            <q-btn v-for="(image, index) in images" :key="index" flat round color="white" :icon="index + 1" @click="slide = image.name" />
          </q-carousel-control>
        </q-carousel>
      </div>
      
      <!-- Contoh Kartu -->
      <div class="q-pa-md row items-start q-gutter-md">
        <q-card class="my-card" flat bordered>
          <q-card-section horizontal>
            <q-card-section class="q-pt-xs">
              <div class="text-overline">Crop top style</div>
              <div class="text-h5 q-mt-sm q-mb-xs">One set</div>
              <div class="text-caption text-grey">
                Ga usah banyak tanya, langsung aja beli
              </div>
            </q-card-section>

            <q-card-section class="col-5 flex flex-center">
              <q-img
                class="rounded-borders"
                src="https://i.pinimg.com/564x/15/12/9f/15129fe38ad7b17ae2fa4de5c8dd2955.jpg" style="width: 200px; height: auto;" />
            </q-card-section>
          </q-card-section>

          <q-separator />

          <q-card-actions>
            <q-btn flat color="primary">Rp.500.000,00</q-btn>
            <q-btn flat round color="yellow" icon="star" />
            <q-btn flat round color="primary" icon="share" />
            <q-btn flat round color="red" icon="shopping_cart" />
          </q-card-actions>
        </q-card>

        <q-card class="my-card">
          <q-card-section horizontal>
            <q-img src="https://i.pinimg.com/474x/e2/d6/bc/e2d6bcd147e761f37e3d510898fd2e0b.jpg" />
            <q-card-section>{{ lorem }}</q-card-section>
          </q-card-section>

          <q-separator />

          <q-card-actions>
            <q-btn flat color="primary">Rp.499.990,00</q-btn>
            <q-btn flat round color="yellow" icon="star" />
              <q-btn flat round color="primary" icon="share" />
            <q-btn flat round color="red" icon="shopping_cart" />
          </q-card-actions>
        </q-card>

        <q-card class="my-card">
          <q-card-section horizontal>
            <q-img
              class="col"
              src="https://i.pinimg.com/564x/9b/05/0e/9b050ec7a457c2e814bbe2d38a311fd8.jpg"
            />
            <q-card-actions vertical class="justify-around">
              <q-btn flat round color="red" icon="shopping_cart" />
              <q-btn flat round color="accent" icon="bookmark" />
              <q-btn flat round color="primary" icon="share" />
            </q-card-actions>
          </q-card-section>
        </q-card>
      </div>
    </q-page-container>

    <q-footer elevated class="bg-purple-8 text-white">
      <q-toolbar class="text-center">
        <!-- Center-align the text -->
        <q-toolbar-title class="text-caption">
          <!-- Apply smaller font size -->
          <div>Copyright © 2024 Harmeilia Reski Rahmayani</div>
        </q-toolbar-title>
      </q-toolbar>
    </q-footer>
  </q-layout>
</template>

<script>
import { ref } from 'vue'

export default {
  setup() {
    const leftDrawerOpen = ref(false)
    const rightDrawerOpen = ref(false)
    const slide = ref('slide-1')
    const images = ref([
      { name: 'slide-1', src: 'https://i.pinimg.com/564x/aa/09/f6/aa09f6be84e9045dbc8be836d6c92a13.jpg' },
      { name: 'slide-2', src: 'https://i.pinimg.com/564x/21/2d/cf/212dcfae5a97cc26b5a234bd7d8a8a54.jpg' },
      { name: 'slide-3', src: 'https://i.pinimg.com/564x/8f/60/06/8f600657922b3b62a3272449b1c1ffdc.jpg' },
    ])

    return {
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value
      },
      rightDrawerOpen,
      toggleRightDrawer() {
        rightDrawerOpen.value = !rightDrawerOpen.value
      },
      slide,
      images,
    }
  },
}
</script>

<style scoped>
.q-tabs__content {
  justify-content: flex-end;
}
.q-toolbar {
  padding-right: 16px; /* Adjust padding to align toolbar with tabs */
}
.text-caption {
  font-size: 12px; /* Adjust font size */
}
.carousel-container {
  max-width: 800px; /* Set max width for carousel */
  margin: 20px auto; /* Center the carousel */
}
.my-card {
  width: 30%; /* Adjust width of the card */
}
.row {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-between;
}
</style>
