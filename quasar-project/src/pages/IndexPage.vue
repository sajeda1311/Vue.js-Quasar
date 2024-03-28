<!-- Main Content Page:  -->

<template>
  <q-page class="flex flex-center">
    <div
      v-for="index in 2"
      :key="index"
      class="q-pa-md items-start q-gutter-md card"
    >
      <div v-for="index in 4" :key="index">
        <q-card class="my-card">
          <img src="/src/assets/mountains.jpg" />
        </q-card>
        <q-item>
          <q-item-section avatar>
            <q-avatar>
              <img src="https://cdn.quasar.dev/img/avatar2.jpg" />
            </q-avatar>
          </q-item-section>

          <q-item-section>
            <q-item-label>video {{ index }}</q-item-label>
            <q-item-label caption>{{ randomNumber }} views</q-item-label>
          </q-item-section>
        </q-item>
      </div>
    </div>
  </q-page>
</template>

<script setup>
defineOptions({
  name: "IndexPage",
  data() {
    return {
      randomNumber: null,
    };
  },
  created() {
    this.randomNumber = Math.floor(Math.random() * 1000); // Generates a random number between 0 and 1000
  },
});
</script>
