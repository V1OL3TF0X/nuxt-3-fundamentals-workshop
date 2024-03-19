<script setup>
const todoList = ref([]);
function fetchTodoList() {
  fetch('https://jsonplaceholder.typicode.com/todos/')
    .then((response) => response.json())
    .then((json) => {
      todoList.value = json;
    });
}
</script>

<template>
  <div>
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
    <h1>Hello Frontend Masters!</h1>
    <button @click="fetchTodoList">Fetch Data</button>
    <ul :class="$style.list">
      <li v-for="todo in todoList" :key="`todo-id-${todo.id}`">
        <input type="checkbox" :checked="todo.completed" /> {{ todo.title }}
      </li>
    </ul>
  </div>
</template>

<style module>
.list {
  display: grid;
  grid-template-columns: 1fr 1fr;
}
</style>
