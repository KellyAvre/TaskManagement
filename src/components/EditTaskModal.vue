<template>
    <div class="edit-task-modal">
      <input v-model="editedTask" @keyup.enter="saveTask" type="text" placeholder="Edit task" />
      <button @click="saveTask">Save</button>
      <button @click="$emit('close')">Cancel</button>
    </div>
  </template>
  
  <script>
  export default {
    name: "EditTaskModal",
    props: {
      task: String,
    },
    data() {
      return {
        editedTask: this.task,
      };
    },
    methods: {
      saveTask() {
        this.$emit("save", this.editedTask);
      },
    },
  };
  </script>
  
  <style scoped>
.edit-task-modal {
  background-color: #fff;
  padding: 20px;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.2);
  border-radius: 5px;
  text-align: center;
}

.edit-task-modal input {
  width: 100%;
  padding: 10px;
  font-size: 16px;
  margin-bottom: 10px;
}

.edit-task-modal button {
  background-color: #3498db;
  color: #fff;
  border: none;
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
}

.edit-task-modal button:hover {
  background-color: #2980b9;
}
</style>
  