<style>
@import '/src/css/styles/inferenceList.css';
@import '/src/css/styles/modelList.css';
</style>

<template>
  <q-page class="window-height row justify-center items-center">
    <h2 class="h2-text text-primary">Modelos</h2>
    <q-card square class="table-card">
      <q-table
        table-class="screenwide"
        title="Modelos disponíveis"
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
const rows = [
  {
    id: "fake_id_1",
    name: "fake_model_1",
    created_in: "31-12-2021",
    version:"1.0.0",
    description:"Descrição breve do modelo ... João amava Teresa que amava Raimundo"+
      "que amava Maria que amava Joaquim que amava Lili,"+
      "que não amava ninguém."+
      "João foi para os Estados Unidos, Teresa para o convento,"+
      "Raimundo morreu de desastre, Maria ficou para tia,"+
      "Joaquim suicidou-se e Lili casou com J. Pinto Fernandes"+
      "que não tinha entrado na história."
  },
  {
    id: "fake_id_2",
    name: "fake_model_2",
    created_in: "31-12-2021",
    version:"1.0.1",
    description:"No meio do caminho tinha uma pedra"+
      "tinha uma pedra no meio do caminho"+
      "tinha uma pedra"+
      "no meio do caminho tinha uma pedra."
  },
  {
    id: "fake_id_3",
    name: "fake_model_3",
    created_in: "31-12-2021",
    version:"2.1.0",
    description: "Nunca me esquecerei desse acontecimento"+
      "na vida de minhas retinas tão fatigadas."+
      "Nunca me esquecerei que no meio do caminho"+
      "tinha uma pedra"+
      "tinha uma pedra no meio do caminho"+
      "no meio do caminho tinha uma pedra."
  },
  {
    id: "fake_id_1",
    name: "fake_model_4",
    created_in: "01-03-2022",
    version:"3.1.0",
    description: "Minha terra tem palmeiras,"+
      "Onde canta o Sabiá;"+
      "As aves, que aqui gorjeiam,"+
      "Não gorjeiam como lá."+
      "Nosso céu tem mais estrelas,"+
      "Nossas várzeas têm mais flores,"+
      "Nossos bosques têm mais vida,"+
      "Nossa vida mais amores."
  },
];

export default {
  setup() {
    return {
      columns,
      rows,
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
};
</script>
