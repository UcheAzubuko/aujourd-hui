<template>
  <base-dialog v-if="inputIsInvalid" @close="confirmError">
  </base-dialog>
  <base-card>
    <form @submit.prevent="submitData">
      <div class="form-control">
        <label for="title">Task Title</label>
        <input type="text" name="title" id="title" ref="titleInput" />
      </div>
      <div class="form-control">
        <label for="description">Task Description</label>
        <textarea
          name="description"
          id="description"
          rows="3"
          ref="descInput"
        ></textarea>
      </div>
      <div class="form-control">
        <base-button type="submit">Add Task</base-button>
      </div>
    </form>
  </base-card>
</template>

<script>
export default {
  inject: ["addTask"],
  data() {
    return {
      inputIsInvalid: false,
    };
  },
  methods: {
    submitData() {
      const enteredTitle = this.$refs.titleInput.value;
      const enteredDesc = this.$refs.descInput.value;

      if (
        enteredTitle.trim() === "" ||
        enteredDesc.trim() === ""
      ) {
        this.inputIsInvalid = true;
        return;
      }
  
      this.addTask(enteredTitle, enteredDesc);
    },
    confirmError() {
      this.inputIsInvalid = false;
    }
  },
};
</script>

<style scoped>
label {
  display: block;
  font-weight: bold;
  margin-bottom: 0.5rem;
}

input,
textarea {
  display: block;
  width: 100%;
  font: inherit;
  padding: 0.15rem;
  border: 1px solid #ccc;
}

input:focus,
textarea:focus {
  outline: none;
  border-color: #3a0061;
  background-color: #f7ebff;
}

.form-control {
  margin: 1rem 0;
}
</style>