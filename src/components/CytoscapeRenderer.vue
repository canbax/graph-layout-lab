<script setup lang="ts">
import { watch, onMounted, onBeforeUnmount } from "vue";
import cytoscape, {
  type Core,
  type ElementsDefinition,
  type LayoutOptions,
  type StylesheetJson,
} from "cytoscape";

const props = defineProps<{
  elements: ElementsDefinition;
  layout?: LayoutOptions;
  style?: StylesheetJson;
}>();

let cy: Core | null = null;

const initCytoscape = () => {
  if (cy) cy.destroy();
  cy = cytoscape({
    container: document.getElementById("cy"),
    elements: props.elements,
    layout: props.layout || { name: "grid" },
    style: props.style || [],
  });
};

onMounted(() => {
  initCytoscape();
});

watch(
  () => props.elements,
  () => {
    initCytoscape();
  },
  { deep: true }
);

onBeforeUnmount(() => {
  if (cy) cy.destroy();
});
</script>

<template>
  <div id="cy"></div>
</template>

<style scoped>
#cy {
  width: 100%;
  height: 100%;
  min-width: 400px;
  min-height: 400px;
  border: 1px solid #ccc;
  background: #fafafa;
  border-radius: 8px;
}
</style>
