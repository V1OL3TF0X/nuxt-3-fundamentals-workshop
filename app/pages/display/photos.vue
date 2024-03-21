<template>
  <div>
    This is main photo LayoutKey
    <NuxtPage />
  </div>
</template>

<style module>
.photo-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  grid-template-rows: 1fr;
  gap: 10px;
}
</style>
