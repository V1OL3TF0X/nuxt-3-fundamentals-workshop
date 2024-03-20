<script setup>
const props = defineProps({
  title: {
    type: String,
    required: true,
  },
  listClass: {
    type: String,
  },
  filter: {
    type: Function,
  },
});
const itemList = ref([]);
const route = useRoute();
onMounted(() =>
  fetch(`https://jsonplaceholder.typicode.com/${route.path.split('/').at(-1)}/`)
    .then((response) => response.json())
    .then((json) => {
      itemList.value = json;
    })
);
const filteredItemList = computed(() =>
  !!props.filter ? itemList.value.filter(props.filter) : itemList.value
);
</script>

<template>
  <div class="section">
    <slot name="hero" />
    <h1 class="title heading">{{ title }}</h1>
    <slot name="metrics" :data="filteredItemList" />
    <ul :class="listClass">
      <li v-for="item in filteredItemList" :key="`todo-id-${item.id}`">
        <slot name="item" :item="item" />
      </li>
    </ul>
  </div>
</template>

<style lang="scss"></style>
