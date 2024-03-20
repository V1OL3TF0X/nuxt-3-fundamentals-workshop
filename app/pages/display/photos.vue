<script setup>
const { query } = useRoute();
const filter = computed(() =>
  query.album ? (photo) => photo.albumId === +query.album : undefined
);
</script>

<template>
  <ListViewer
    title="Photo Gallery"
    :list-class="$style['photo-grid']"
    :filter="filter"
  >
    <template #metrics="{ data }"> {{ data.length }} photos </template>
    <template #item="{ item: photo }">
      <h6>{{ photo.title }}</h6>
      <img :src="photo.thumbnailUrl" />
    </template>
  </ListViewer>
</template>

<style module>
.photo-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  grid-template-rows: 1fr;
  gap: 10px;
}
</style>
