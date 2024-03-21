<script setup>
const { query } = useRoute();
const filter = computed(() =>
  query.completed
    ? (todo) => todo.completed === (query.completed === 'true')
    : undefined
);
</script>

<template>
  <ListViewer
    title="Hello Frontend Masters!"
    :list-class="$style.list"
    :filter="filter"
  >
    <template #hero>
      <img src="/todo.jpg" alt="Todo photo by Glenn Casterns-Peters" />
      <p>
        Photo by
        <a
          href="https://unsplash.com/@glenncarstenspeters?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText"
          >Glenn Carstens-Peters</a
        >
        on
        <a
          href="https://unsplash.com/s/photos/todo?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText"
          >Unsplash</a
        >
      </p>
    </template>
    <template #item="{ item: todo }">
      <input type="checkbox" :checked="todo.completed" />
      <NuxtLink :to="`/display/todos/${todo.id}`">{{ todo.title }}</NuxtLink>
    </template>
  </ListViewer>
</template>

<style lang="scss" module>
@import './assets/styles/main.scss';
:root {
  --text-color: #{$textColor};
}
.heading {
  color: var(--text-color);
}

.list {
  color: var(--text-color);
  display: grid;
  grid-template-columns: 1fr 1fr;
}
</style>
