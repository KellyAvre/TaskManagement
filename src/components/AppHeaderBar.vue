<template>
  <header class="app-header">
    <h1>Task Management App</h1>
  </header>
</template>

<script>
export default {
  name: "AppHeaderBar",
};
</script>

<style scoped>
.app-header {
  background-color: #279b61;
  color: #fff;
  padding: 20px;
  text-align: center;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
}

.app-header h1 {
  font-size: 24px;
  margin: 0;
}
/* Media query for smaller screens */
@media (max-width: 768px) {
  .app-header {
    padding: 10px;
  }

  .app-header h1 {
    font-size: 18px;
  }
}
</style>
