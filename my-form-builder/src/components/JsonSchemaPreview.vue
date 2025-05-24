<script setup>
import { defineProps } from "vue";

const props = defineProps({
  fields: { type: Array, required: true },
});

function generateJSON(field) {
  return JSON.stringify(field, null, 3);
}
</script>

<template>
  <div class="main-column">
    <h1>JSON</h1>
    <div class="text-container">
      <pre>{{ generateJSON(fields) }}</pre>
    </div>
  </div>
</template>

<style scoped>
.text-container {
  width: 95%;
  border: 1px solid;
  background-color: aquamarine;
  margin: auto;
  height: 90%;
  overflow-y: auto;
}
</style>
