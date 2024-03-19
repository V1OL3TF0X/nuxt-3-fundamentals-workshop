<script setup>
import { ref, computed } from 'vue';
const photoList = ref([]);
const photoCount = computed(() => {
  return photoList.value.length;
});

function fetchPhotoGallery() {
  fetch('https://jsonplaceholder.typicode.com/photos')
    .then((response) => response.json())
    .then((json) => {
      photoList.value = json;
    });
}
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
