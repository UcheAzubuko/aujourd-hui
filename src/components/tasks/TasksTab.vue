<template>
  <base-card>
    <base-button
      @click="setCurrentTab('stored-tasks')"
      :mode="storedTasksMode"
      >Stored Tasks</base-button
    >
    <base-button @click="setCurrentTab('add-task')" :mode="addTaskMode"
      >Add Task</base-button
    >
  </base-card>
  <component :is="currentTab"></component>
</template>

<script>
import StoredTasks from "./StoredTasks.vue";
import AddTask from "./AddTask.vue";

export default {
  components: {
    StoredTasks,
    AddTask,
  },
  data() {
    return {
      currentTab: "stored-tasks",
      storedTasks: [],
    };
  },
  provide() {
    return {
      tasks: this.storedTasks,
      addTask: this.addTask,
      deleteTask: this.deleteTask,
    };
  },
  computed: {
    storedTasksMode() {
      return this.currentTab === "stored-tasks" ? null : "flat";
    },
    addTaskMode() {
      return this.currentTab === "add-task" ? null : "flat";
    },
  },
  methods: {
    setCurrentTab(tab) {
      this.currentTab = tab;
    },
    addTask(title, description) {
      const newTask = {
        id: new Date().toISOString(),
        title: title,
        description: description,
      };
      this.storedTasks.unshift(newTask);
      this.currentTab = "stored-tasks";
    },
    deleteTask(taskId) {
      const taskIndex = this.storedTasks.findIndex(
        (task) => task.id === taskId
      );
      this.storedTasks.splice(taskIndex, 1);
    },
  },
};
</script>