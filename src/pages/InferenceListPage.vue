<style>
  @import '/src/css/styles/inferenceList.css';
</style>

<template>
  <q-page class="window-height row justify-center items-center">
    <h2 class="h2-text text-primary">Inferências</h2>
    <q-card square class="table-card">
      <q-table
        table-class="screenwide"
        title="Minhas inferências"
        :rows="rows"
        :columns="columns"
        row-key="name"
        @row-click="onRowClick"
        class="table text-h4"
        virtual-scroll
        v-model:pagination="pagination"
        :rows-per-page-options="[0]"
      />
    </q-card>
    <q-dialog v-model="card">
      <q-card>
        <div v-if="selected_row.status == 'processing'">
          <q-card-section class="result-header-processing q-py-xl">
            <a class="text-h4 text-white">Resultado</a>
          </q-card-section>
        </div>
        <div v-else-if="selected_row.status == 'completed'">
          <q-card-section class="result-header-completed q-py-xl">
            <a class="text-h4 text-white">Resultado</a>
          </q-card-section>
        </div>
        <div v-else>
          <q-card-section class="result-header-error q-py-xl">
            <a class="text-h4 text-white">Resultado</a>
          </q-card-section>
        </div>
        <q-card-section class="row q-px-xl q-py-md items-center" horizontal>
          <q-card class="q-px-md orientation-landscape" bordered>
            <p class="text-body1 text-no-wrap"><b>Modelo:</b></p>
            <p>{{ selected_row.model }}</p>
            <p class="text-body1 text-no-wrap"><b>Idade:</b></p>
            <p>{{ selected_row.age }}</p>
            <p class="text-body1 text-no-wrap"><b>Sexo:</b></p>
            <p>{{ selected_row.sex }}</p>
            <p class="text-body1 text-no-wrap">
              <b>Nível de falta de ar:</b>
            </p>
            <p>
              {{ selected_row.breathlessness_level }}
            </p>
            <p class="text-body1 text-no-wrap">
              <b>Criado em:</b>
            </p>
            <p>{{ selected_row.created_in }}</p>
          </q-card>
          <q-space style="width:25px" class="orientation-landscape"/>
          <q-card class="q-pb-xl text-center status-card">
            <div v-if="selected_row.status == 'processing'">
              <h6 class="text-body1 q-py-sm">Inferência em andamento...</h6>
              <q-spinner-hourglass color="accent" size="10em" />
            </div>
            <div v-else-if="selected_row.status == 'error'">
              <h6 class="text-body1">Ocorreu um erro na inferência</h6>
              <q-icon name="report_problem" color="negative" size="8em" />
            </div>
            <div v-else>
              <h6 class="text-body1 q-py-sm">
                Inferência realizada com sucesso
              </h6>
              <q-icon name="task_alt" color="info" size="10em" />
            </div>
          </q-card>
        </q-card-section>
        <q-card-section class="bg-secondary" v-if="selected_row.status == 'completed'">
          <h6 class="text-body1 q-py-sm"><b>Diagnóstico:</b></h6>
        </q-card-section>
        <q-card-section class="bg-warning" v-else-if="selected_row.status == 'error'">
          <h6 class="text-body1 q-py-sm"><b>Detalhes:</b></h6>
        </q-card-section>
      </q-card>
    </q-dialog>
  </q-page>
</template>



<script>
import { ref } from "vue";
import { api } from "/src/boot/axios";

const columns = [
  {
    name: "model",
    required: true,
    label: "Modelo",
    align: "center",
    field: (row) => row.model,
    format: (val) => `${val}`,
    sortable: true,
  },
  {
    name: "age",
    align: "center",
    label: "Idade",
    field: "age",
    sortable: true,
  },
  {
    name: "sex",
    align: "center",
    label: "Sexo",
    field: "sex",
    sortable: true,
  },
  {
    name: "breathlessness_level",
    align: "center",
    label: "Nível de falta de ar",
    field: "breathlessness_level",
    sortable: true,
  },
  {
    name: "created_in",
    align: "center",
    label: "Criado em",
    field: "created_in",
    sortable: true,
  },
  { name: "status", align: "center", label: "Status", field: "status" },
];

const result = { diagnosis: false };

export default {
  setup() {
    return {
      columns,
      rows:ref([]),
      selected_row: ref({}),
      results: ref({}),
      card: ref(false),
    };
  },
  methods: {
    onRowClick(evt, row) {
      this.selected_row = row;
      this.card = true;
      this.results = result;
    },
  },
  mounted () {
    api
      .get('/v1/users/fake_user_id/inferences')
      .then(response =>{this.rows=response.data.inferences})
  }
};
</script>
