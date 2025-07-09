<script setup lang="ts">
import type { ElementsDefinition } from "cytoscape";
import CytoscapeRenderer from "./components/CytoscapeRenderer.vue";

const elements: ElementsDefinition = {
  nodes: [
    {
      data: { id: "a" },
    },
    {
      data: { id: "b" },
    },
  ],
  edges: [
    {
      data: { id: "ab", source: "a", target: "b" },
    },
  ],
};
</script>

<template>
  <v-layout>
    <v-app-bar prominent>
      <template #prepend> </template>

      <template #title>
        <v-app-bar-title> Graph Layout Lab </v-app-bar-title>
      </template>

      <template #default>
        <v-btn
          variant="outlined"
          class="text-capitalize ma-2"
          prepend-icon="mdi-github"
        >
          GitHub
        </v-btn>
      </template>

      <template #append>
        <v-btn
          variant="outlined"
          class="text-capitalize ma-2"
          prepend-icon="mdi-github"
        >
          GitHub 22
        </v-btn>
      </template>
    </v-app-bar>

    <v-main>
      <CytoscapeRenderer msg="Vite + Vue" :elements="elements" />
    </v-main>
  </v-layout>

  <div class="cy-container"></div>
</template>

<style scoped>
.cy-container {
  width: 100%;
  height: 100vh;
}
</style>
