<!-- Main Layout code:  -->

<template>
  <div class="q-pa-md">
    <q-layout view="hHh Lpr lff" style="height: 300px" class="rounded-borders">
      <q-header elevated>
        <q-toolbar>
          <div class="menu-toggle">
            <q-btn
              flat
              dense
              round
              icon="menu"
              aria-label="Menu"
              @click="drawer = !drawer"
            />
            <img src="/src/assets/youtube1.png" alt="youtube" class="youtube" />
          </div>

          <div class="menu-toggle w-100 mr-120">
            <q-input
              placeholder="Search"
              v-model="searchTerm"
              @keyup.enter="search"
              append
              class="w-100 search-field"
            >
              <q-icon
                name="keyboard"
                size="lg"
                @click="toggleKeyboard"
                class="keyboard"
              />
              <template v-slot:append>
                <q-icon name="search" />
              </template>
            </q-input>
            <q-icon name="mic" @click="voiceSearch" class="voice-icon" />
          </div>
          <div class="menu-toggle">
            <q-btn flat round dense icon="more_vert" />
            <q-btn round>
              <q-avatar size="42px">
                <img src="https://cdn.quasar.dev/img/avatar2.jpg" />
              </q-avatar>
            </q-btn>
          </div>
        </q-toolbar>
      </q-header>

      <q-drawer
        v-model="drawer"
        show-if-above
        :mini="miniState"
        @mouseover="miniState = false"
        @mouseout="miniState = true"
        :width="200"
        :breakpoint="500"
      >
        <q-scroll-area class="fit" :horizontal-thumb-style="{ opacity: 0 }">
          <q-list padding>
            <EssentialLink
              v-for="link in linksList"
              :key="link.title"
              v-bind="link"
            />
          </q-list>
        </q-scroll-area>
      </q-drawer>

      <q-page-container class="main-page-content">
        <router-view />
      </q-page-container>
    </q-layout>
  </div>
</template>

<script setup>
import { ref } from "vue";
import EssentialLink from "components/EssentialLink.vue";

defineOptions({
  name: "MainLayout",
  data() {
    return {
      searchTerm: "",
      drawer: ref(false),
      miniState: ref(true),
    };
  },
  methods: {
    search() {
      // Search functionality
      console.log("Searching for:", this.searchTerm);
      // search logic
    },
    toggleKeyboard() {
      // Keyboard toggle functionality
      console.log("Toggle keyboard");
      // Keyboard toggle logic
    },
  },
});

const linksList = [
  {
    title: "Home",
    icon: "home",
    link: "https://www.youtube.com/",
  },
  {
    title: "Shorts",
    icon: "tv",
    link: "https://www.youtube.com/",
  },
  {
    title: "Subscriptions",
    icon: "subscriptions",
    link: "https://www.youtube.com/",
  },
  {
    title: "History",
    icon: "history",
    link: "https://www.youtube.com/",
  },
];

const leftDrawerOpen = ref(false);

function toggleLeftDrawer() {
  leftDrawerOpen.value = !leftDrawerOpen.value;
}
</script>
