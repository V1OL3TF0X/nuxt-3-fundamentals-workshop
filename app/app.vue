<script>
import PhotoGallery from './photo-gallery.vue';
import AppTodo from './app-todo.vue';
import { defineNuxtComponent } from '#app';

export default defineNuxtComponent({
  components: { PhotoGallery, AppTodo },
});
</script>

<template>
  <PhotoGallery />
  <AppTodo />
</template>

<style></style>
