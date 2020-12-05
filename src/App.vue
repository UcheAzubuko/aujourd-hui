<template>
  <the-header title="Aujourd'hui"></the-header>
  <div class="app-container">
    <tasks-tab></tasks-tab>
  </div>
</template>

<script>
import TheHeader from "./components/layouts/TheHeader.vue";
import TasksTab from "./components/tasks/TasksTab.vue";
export default {
  components: {
    TheHeader,
    TasksTab,
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Nunito&display=swap");

* {
  margin: 0;
  box-sizing: border-box;
}

html {
  font-family: "Nunito", sans-serif;
}

a {
  text-decoration: none;
}

.app-container {
  max-width: 40rem;
  margin: auto;
  padding: 0 1rem;
  overflow: hidden;
}

ul {
  list-style: none;
  padding: 0;
}
</style>
