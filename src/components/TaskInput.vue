<template>
  <div class="task-input">
    <input v-model="newTask" @keyup.enter="addTask" type="text" placeholder="Add a new task" />
    <button @click="addTask">Add</button>
  </div>
</template>

<script>
export default {
  name: "TaskInput",
  data() {
    return {
      newTask: "",
    };
  },
  methods: {
    addTask() {
      this.$emit("add-task", this.newTask);
      this.newTask = "";
    },
  },
};
</script>


<style scoped>
.task-input {
  display: flex;
  margin-bottom: 20px;
  background-color: #27ae60; /* A powerful green color */
}

.task-input input {
  flex: 1;
  padding: 10px;
  font-size: 16px;
}

.task-input button {
  background-color: #27ae60;
  color: #fff;
  border: none;
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
}

.task-input button:hover {
  background-color: #219d54;
}


/* Media query for smaller screens */
@media (max-width: 768px) {
  .task-input {
    flex-direction: column;
    align-items: stretch;
  }

  .task-input input {
    margin-bottom: 10px;
  }
}
</style>