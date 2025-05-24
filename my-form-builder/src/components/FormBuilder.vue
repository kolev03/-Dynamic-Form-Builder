<script setup>
import "../style.css";
import { defineProps, defineEmits } from "vue";

const emit = defineEmits(["remove"]);

let props = defineProps({
  fields: { type: Array, required: true },
});

function removeField(id) {
  emit("remove", id);
}

function changeValue(id, event) {
  const newValue = event.target.value;

  emit("update", { id, value: newValue });
}
</script>

<template>
  <div class="main-column">
    <h1>Form Builder</h1>
    <div v-for="field in fields" :key="field.id" class="form-field">
      <input
        v-if="field.type === 'text'"
        type="text"
        :placeholder="field.label"
        @change="changeValue(field.id, $event)"
      />
      <input
        v-else-if="field.type === 'date'"
        type="date"
        @change="changeValue(field.id, $event)"
      />
      <select v-else @change="changeValue(field.id, $event)">
        <option>Option 1</option>
        <option>Option 2</option>
      </select>

      <button type="button" @click="removeField(field.id)">Remove</button>
    </div>
  </div>
</template>

<style scoped>
.form-field {
  width: 90%;
  margin: auto;
  display: flex;
  justify-content: space-between;
  margin-bottom: 10px;
  border: 1px solid black;
  padding: 2px;
}

input,
select {
  border: none;
  font-size: 1.25rem;
}

button {
  background-color: red;
  font-size: 1rem;
  color: white;
  border: none;
  padding: 3px;
}

button:hover {
  cursor: pointer;
  background-color: rgb(189, 9, 9);
}
</style>
