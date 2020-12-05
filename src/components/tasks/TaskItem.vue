<template>
  <li>
    <base-card>
      <header>
        <h3>{{ title }}</h3>
        <base-button mode="flat" @click="deleteTask(id)">Delete</base-button>
      </header>
      <p>{{ description }}</p>
    </base-card>
  </li>
</template>

<script>
export default {
  props: ["id", "title", "description"],
  inject: ["deleteTask"],
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
</style>