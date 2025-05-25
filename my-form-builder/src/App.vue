<script setup>
import FieldPallet from "./components/FieldPallet.vue";
import FormBuilder from "./components/FormBuilder.vue";
import JsonSchemaPreview from "./components/JsonSchemaPreview.vue";
import { ref } from "vue";

const fields = ref([]);
let idForm = 0;

function handleAdd(btn) {
  idForm++;
  let labelValue = "";
  if (btn.type === "date") {
    labelValue = "No Date Selected";
  } else if (btn.type === "select") {
    labelValue = "Option 1";
  } else if (btn.type === "text") {
    labelValue = btn.label;
  }
  fields.value.push({
    id: idForm,
    type: btn.type,
    label: labelValue,
  });
}

function removeField(id) {
  fields.value = fields.value.filter((field) => field.id !== id);
}

function updateField({ id, value }) {
  const field = fields.value.find((field) => field.id === id);
  if (field) field.label = value;
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
