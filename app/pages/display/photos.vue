<template>
  <ListViewer title="Photo Gallery" :list-class="$style['photo-grid']">
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
