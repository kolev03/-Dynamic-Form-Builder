<script setup>
import { ref } from "vue";

const buttons = ref([
  { label: "Text Input", type: "text" },
  { label: "Date Picker", type: "date" },
  { label: "Dropdown", type: "select" },
]);

function addField(params) {
  console.log(params);
}
</script>

<template>
  <div class="main-column">
    <h1>Field Pallet</h1>
    <div class="buttons">
      <button
        v-for="btn in buttons"
        :key="btn.type"
        @click="addField(btn.type)"
      >
        {{ btn.label }}
      </button>
    </div>
  </div>
</template>

<style scoped>
.buttons {
  display: flex;
  width: 80%;
  margin: auto;
  flex-direction: column;
  gap: 10px;
}

button {
  font-size: 1.25rem;
}
</style>
