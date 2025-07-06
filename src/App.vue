<script setup lang="ts">
import CytoscapeRenderer from "./components/CytoscapeRenderer.vue";

const elements = [
  {
    data: { id: "a" },
  },
  {
    data: { id: "b" },
  },
  {
    data: { id: "ab", source: "a", target: "b" },
  },
];
</script>

<template>
  <div class="cy-container">
    <CytoscapeRenderer msg="Vite + Vue" :elements="elements" />
  </div>
</template>

<style scoped>
.cy-container {
  width: 100%;
  height: 100vh;
}
</style>
