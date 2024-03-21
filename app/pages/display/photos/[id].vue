<script setup>
const photo = ref();
const route = useRoute();
onMounted(() =>
  fetch(`https://jsonplaceholder.typicode.com/photos/${route.params.id}`)
    .then((response) => response.json())
    .then((json) => {
      photo.value = json;
    })
);
</script>

<template>
  <div>
    Fancy photo page
    <div class="loader" v-if="!photo"></div>
    <div v-else :class="$style['img-container']">
      <img :src="photo.url" />
      <div :class="$style.description">
        <h4 class="title">{{ photo.title }}</h4>
        <p>from album {{ photo.albumId }}</p>
      </div>
    </div>
  </div>
</template>

<style lang="scss" module>
.img-container {
  position: relative;
}

.description {
  position: absolute;
  bottom: 0;
  left: 0;
}
</style>
