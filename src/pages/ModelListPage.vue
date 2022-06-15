<style>
@import '/src/css/styles/inferenceList.css';
@import '/src/css/styles/modelList.css';
</style>

<template>
  <q-page class="window-height row justify-center items-center">
    <h2 class="h2-text text-primary">Modelos</h2>
    <ListTable
    title="Modelos disponíveis"
        :rows="rows"
        :columns="columns"/>
    <q-dialog v-model="card">
      <q-card>
        <q-card-section class="result-header q-py-xl">
          <a class="text-h4 text-white">Descrição</a>
        </q-card-section>
        <q-card-section class="row q-px-xl q-py-md items-center" horizontal>
          <p align="justify" class="text-body1">
            {{selected_row.description}}
          </p>
        </q-card-section>
      </q-card>
    </q-dialog>
  </q-page>
</template>



<script>
import { ref } from "vue";
import { api } from "/src/boot/axios";
import ListTable from "components/ListTable.vue";

const columns = [
  {
    name: "model",
    required: true,
    label: "Nome",
    align: "center",
    field: (row) => row.name,
    format: (val) => `${val}`,
    sortable: true,
  },
  {
    name: "created_in",
    align: "center",
    label: "Criado em",
    field: "created_in",
    sortable: true,
  },
  {
    name: "version",
    align: "center",
    label: "Versão",
    field: "version",
    sortable: true,
  },
];

export default {
  components: {
    ListTable
  },
  setup() {
    return {
      columns,
      rows:ref([]),
      selected_row: ref({}),
      card: ref(false),
    };
  },
  methods: {
    onRowClick(evt, row) {
      this.selected_row = row;
      this.card = true;
    },
  },
  mounted () {
    api
      .get('/v1/models')
      .then(response =>{this.rows=response.data.models})
  }
};
</script>
