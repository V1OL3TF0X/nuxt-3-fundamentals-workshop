<script>
import { defineNuxtComponent } from '#app';

export default defineNuxtComponent({
  data: () => ({
    photoList: [],
  }),
  methods: {
    fetchPhotoGallery() {
      fetch('https://jsonplaceholder.typicode.com/photos')
        .then((response) => response.json())
        .then((json) => {
          this.photoList = json;
        });
    },
  },
  computed: {
    photoCount() {
      return this.photoList.length;
    },
  },
});
</script>

<template>
  <h1>Photo Gallery ({{ photoCount }} photos)</h1>
  <button @click="fetchPhotoGallery">Fetch Data</button>
  <div
    style="
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
      grid-template-rows: 1fr;
      gap: 10px;
    "
  >
    <div v-for="photo in photoList" :key="`photo-${photo.id}`">
      <h6>{{ photo.title }}</h6>
      <img :src="photo.thumbnailUrl" />
    </div>
  </div>
</template>
