<script setup>
const props = defineProps({
  title: {
    type: String,
    required: true,
  },
  itemType: {
    type: String,
    required: true,
  },
  listClass: {
    type: String,
  },
});
const itemList = ref([]);
function fetchItemList() {
  fetch(`https://jsonplaceholder.typicode.com/${props.itemType}/`)
    .then((response) => response.json())
    .then((json) => {
      itemList.value = json;
    });
}
</script>

<template>
  <div class="section">
    <slot name="hero" />
    <h1 class="title heading">{{ title }}</h1>
    <slot name="metrics" :data="itemList" />
    <button @click="fetchItemList">Fetch Data</button>
    <ul :class="listClass">
      <li v-for="item in itemList" :key="`todo-id-${item.id}`">
        <slot name="item" :item="item" />
      </li>
    </ul>
  </div>
</template>

<style lang="scss"></style>
