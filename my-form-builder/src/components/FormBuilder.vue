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
</script>

<template>
  <div class="main-column">
    <h1>Form Builder</h1>
    <div v-for="field in fields" :key="field.id" class="form-field">
      <input
        v-if="field.type === 'text'"
        type="text"
        :placeholder="field.label"
      />
      <input v-else-if="field.type === 'date'" type="date" />
      <select v-else>
        <option>Option 1</option>
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
</style>
