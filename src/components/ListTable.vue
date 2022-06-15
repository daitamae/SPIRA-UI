<style>
  @import '/src/css/styles/inferenceList.css';
</style>

<template>
  <q-card square class="table-card">
    <q-table
      :title="title"
      :rows="rows"
      :columns="columns"
      table-class="screenwide"
      class="table text-h4"
      virtual-scroll
      v-model:pagination="pagination"
      :rows-per-page-options="[0]"
    />
  </q-card>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  name: "ListTable",
  props: {
    title: {
      type: String,
    },
    rows: {
      type: Array,
      default: ()=>[],
    },

    columns: {
      type: Array,
      default: ()=>[],
    },
  },
});
</script>
