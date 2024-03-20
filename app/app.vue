<script setup>
import PhotoGallery from './components/photo-gallery';
import AppTodo from './components/TodoViewer';
</script>

<template>
  <div class="columns">
    <div class="column">
      <PhotoGallery />
    </div>
    <div class="column">
      <AppTodo title="asdkjalskdj" />
    </div>
  </div>
</template>

<style lang="scss">
@use './node_modules/bulma/bulma.sass';
</style>
