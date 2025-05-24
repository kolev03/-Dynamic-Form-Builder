<script setup>
import FieldPallet from "./components/FieldPallet.vue";
import FormBuilder from "./components/FormBuilder.vue";
import JsonSchemaPreview from "./components/JsonSchemaPreview.vue";
import { ref } from "vue";

const fields = ref([]);

let idForm = 0;

function handleAdd(btn) {
  idForm++;
  fields.value.push({
    id: idForm,
    type: btn.type,
    label: `New ${btn.label}`,
  });
}

function removeField(id) {
  fields.value = fields.value.filter((field) => field.id !== id);
}

function updateField({ id, value }) {
  const f = fields.value.find((f) => f.id === id);
  if (f) f.value = value;
}
</script>

<template>
  <div class="main-body">
    <FieldPallet @add="handleAdd" />
    <FormBuilder @remove="removeField" :fields="fields" @update="updateField" />
    <JsonSchemaPreview :fields="fields"></JsonSchemaPreview>
  </div>
</template>

<style scoped></style>
