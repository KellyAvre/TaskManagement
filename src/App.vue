<template>
  <div>
    <AppHeaderBar />
    <div class="container">
      <TaskInput @add-task="addTask" />
      <TaskList :tasks="tasks" @delete-task="deleteTask" @edit-task="editTask" @change-status="changeStatus" />

      <!-- Edit Task Modal -->
      <EditTaskModal
        v-if="showEditModal"
        :task="tasks[editTaskIndex].text"
        @close="closeEditModal"
        @save="saveEditedTask"
      ></EditTaskModal>
    </div>
  </div>
</template>

<script>
import AppHeaderBar from './components/AppHeaderBar.vue'
import TaskInput from './components/TaskInput.vue'
import TaskList from './components/TaskList.vue'
import EditTaskModal from "@/components/EditTaskModal.vue";

export default {
  name: "App",
  components: {
    AppHeaderBar,
    TaskInput,
    TaskList,
    EditTaskModal,
  },
  data() {
    return {
      tasks: [], // Array to store tasks
      showEditModal: false, // Control the visibility of the edit modal
      editTaskIndex: -1, // Index of the task being edited (-1 means no task is being edited)
    };
  },
  methods: {
    addTask(newTask) {
      if (newTask.trim() === "") {
        // Prevent adding empty tasks
        return;
      }
      this.tasks.push({ id: Date.now(), text: newTask });
    },
    deleteTask(taskId) {
      this.tasks = this.tasks.filter((task) => task.id !== taskId);
    },
    editTask(index) {
      this.showEditModal = true;
      this.editTaskIndex = index;
    },
    closeEditModal() {
      this.showEditModal = false;
      this.editTaskIndex = -1;
    },
    saveEditedTask(editedTask) {
      this.tasks[this.editTaskIndex].text = editedTask;
      this.showEditModal = false;
      this.editTaskIndex = -1;
    },
    changeStatus(task, newStatus) {
      // Update the task status
      task.status = newStatus;
    },
  },
};
</script>

<style>
/* Add your global styling here */
.container {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
}
</style>
