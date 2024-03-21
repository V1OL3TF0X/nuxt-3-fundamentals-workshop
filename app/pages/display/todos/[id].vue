<script setup>
const todo = ref();
const route = useRoute();
onMounted(() =>
  fetch(`https://jsonplaceholder.typicode.com/todos/${route.params.id}`)
    .then((response) => response.json())
    .then((json) => {
      todo.value = json;
    })
);
</script>

<template>
  <div>
    Child page with a single todo:
    <div class="loader" v-if="!todo"></div>
    <pre v-else>
      {{ todo }}
    </pre>
  </div>
</template>
