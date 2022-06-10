<template>
  <q-page class="window-height row justify-center items-center">
    <h2 class="h2-text text-primary">Inferências</h2>
    <q-card square>
      <q-table
        table-class="screenwide"
        title="Minhas inferências"
        :rows="rows"
        :columns="columns"
        row-key="name"
        @row-click="rowclick(evt, row)"
        class="table text-h4"
        virtual-scroll
        v-model:pagination="pagination"
        :rows-per-page-options="[0]"
      />
    </q-card>
  </q-page>
</template>

<style>
.q-card {
  min-width: 95%;
  max-width: 95%;
  width: 1000px;
  height: 800px;
  max-height: 95%;
}

.table {
  height: 800px;
}

.screenwide {
  max-width: 100%;
}

.screenwide .q-table {
  max-width: 100%;
  max-height: 100px;
}

.screenwide td {
  white-space: normal;
  word-wrap: normal;
  hyphens: manual;
}

.screenwide th {
  text-align: center;
}
</style>

<script>
import { ref } from "vue";
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
    name: "brethlessness_level",
    align: "center",
    label: "Nível de falta de ar",
    field: "brethlessness_level",
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
const rows = [
  {
    model: "fake_model_1",
    age: 20,
    sex: "M",
    brethlessness_level: 5,
    created_in: "31-12-2021",
    status: "completed",
  },
  {
    model: "fake_model_2",
    age: 23,
    sex: "F",
    brethlessness_level: 5,
    created_in: "31-12-2021",
    status: "completed",
  },
  {
    model: "fake_model_2",
    age: 23,
    sex: "F",
    brethlessness_level: 5,
    created_in: "31-12-2021",
    status: "processing",
  },
  {
    model: "fake_model_2",
    age: 23,
    sex: "F",
    brethlessness_level: 10,
    created_in: "01-03-2022",
    status: "error",
  },
  {
    model: "fake_model_3",
    age: 23,
    sex: "F",
    brethlessness_level: 4,
    created_in: "31-12-2021",
    status: "completed",
  },
  {
    model: "fake_model_2",
    age: 62,
    sex: "M",
    brethlessness_level: 1,
    created_in: "31-12-2021",
    status: "processing",
  },
  {
    model: "fake_model_1",
    age: 20,
    sex: "M",
    brethlessness_level: 5,
    created_in: "31-12-2021",
    status: "completed",
  },
  {
    model: "fake_model_2",
    age: 23,
    sex: "F",
    brethlessness_level: 5,
    created_in: "31-12-2021",
    status: "completed",
  },
  {
    model: "fake_model_2",
    age: 23,
    sex: "F",
    brethlessness_level: 5,
    created_in: "31-12-2021",
    status: "processing",
  },
  {
    model: "fake_model_2",
    age: 23,
    sex: "F",
    brethlessness_level: 10,
    created_in: "01-03-2022",
    status: "error",
  },
  {
    model: "fake_model_3",
    age: 23,
    sex: "F",
    brethlessness_level: 4,
    created_in: "31-12-2021",
    status: "completed",
  },
  {
    model: "fake_model_2",
    age: 62,
    sex: "M",
    brethlessness_level: 1,
    created_in: "31-12-2021",
    status: "processing",
  },
];
export default {
  setup() {
    return { filter: ref(""), columns, rows };
  },
  rowclick(evt, row) {
    alert("clicked");
  },
};
</script>
