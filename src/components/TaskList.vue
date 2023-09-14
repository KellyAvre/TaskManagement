<template>
  <div>
    <ul class="task-list">
      <li v-for="(task, index) in tasks" :key="task.id">
        
        {{ task.text }}
        <button @click="deleteTask(task.id)">Delete</button>
        <button @click="editTask(index)">Edit</button>
        <button @click="changeStatus(task, 'In Progress')">Start</button>
        <button @click="changeStatus(task, 'Done')">Finish</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "TaskList",
  props: {
    tasks: Array,
  },
  methods: {
    deleteTask(taskId) {
      this.$emit("delete-task", taskId);
    },
    editTask(index) {
      this.$emit("edit-task", index);
    },
    changeStatus(task, newStatus) {
      task.status = newStatus;
      this.$emit("change-status", task);
    },
  },
};
</script>
<style scoped>
.task-list {
  list-style: none;
  padding: 0;
}

.task-list li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  border: 1px solid #ccc;
  /* background-color: #fff; */
  background-color: #26c4ca88; /* A powerful orange color */
  padding: 10px;
  margin-bottom: 10px;
  box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
}

.task-list li span {
  flex: 1;
  font-size: 16px;
}

.task-list button {
  background-color: #e74c3c;
  color: #fff;
  border: none;
  padding: 5px 10px;
  font-size: 14px;
  cursor: pointer;
}

.task-list button:hover {
  background-color: #c0392b;
}
</style>