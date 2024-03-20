<script setup>
const props = defineProps({
  title: {
    type: String,
    required: true,
  },
  listClass: {
    type: String,
  },
});
const itemList = ref([]);
const route = useRoute();
fetch(
  `https://jsonplaceholder.typicode.com/${route.fullPath.split('/').at(-1)}/`
)
  .then((response) => response.json())
  .then((json) => {
    itemList.value = json;
  });
</script>

<template>
  <div class="section">
    <slot name="hero" />
    <h1 class="title heading">{{ title }}</h1>
    <slot name="metrics" :data="itemList" />
    <ul :class="listClass">
      <li v-for="item in itemList" :key="`todo-id-${item.id}`">
        <slot name="item" :item="item" />
      </li>
    </ul>
  </div>
</template>

<style lang="scss"></style>
