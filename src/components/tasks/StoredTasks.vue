<template>
  <ul>
    <task-item
      v-for="task in tasks"
      :key="task.id"
      :id="task.id"
      :title="task.title"
      :description="task.description"
    ></task-item>
  </ul>
</template>

<script>
import TaskItem from "./TaskItem.vue";
export default {
  components: {
    TaskItem,
  },
  inject: ["tasks"],
};
</script>