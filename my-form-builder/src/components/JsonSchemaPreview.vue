<script setup>
import { defineProps } from "vue";

const props = defineProps({
  fields: { type: Array, required: true },
});

function generateJSON(fields) {
  console.log(fields);
  return JSON.stringify(fields, null, 2);
}

function generateJSONwithoutID(field) {
  const { id, ...noId } = field;
  return JSON.stringify(noId, null, 2);
}
</script>

<template>
  <div class="main-column">
    <h1>JSON</h1>
    <div class="text-container">
      <!-- Displaying the JSON with the id, but not in JSON brackets -->
      <!-- <pre v-for="field in fields" :key="field.id">{{
        generateJSONwithoutID(field)
      }}</pre> -->

      <!-- Displaying the JSON without id, but in JSON brackets -->
      <pre>{{ generateJSON(fields) }}</pre>
    </div>
  </div>
</template>

<style scoped>
.text-container {
  width: 95%;
  border: 1px solid;
  background-color: rgb(231, 228, 228);
  margin: 20px auto;
  height: 87%;
  overflow-y: auto;
}

@media screen and (max-width: 1150px) {
  .text-container {
    height: 60%;
  }
}
</style>
