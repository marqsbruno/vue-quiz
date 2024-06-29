<script setup></script>

<template>
  <header>
    <h4>Question 1/3</h4>
    <div class="bar">
      <div class="completion"></div>
    </div>
  </header>
</template>

<style scoped>
.header {
  margin-top: 20px;
}

header h4 {
  font-size: 30px;
}

.bar {
  width: 300px;
  height: 30px;
  border: 2px solid chartreuse;
}

.completion {
  height: 100%;
  width: 0%;
  background-color: yellow;
}
</style>
