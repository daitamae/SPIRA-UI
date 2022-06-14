<template>
  <q-page class="window-height window-width row justify-center items-center"
  style="background: linear-gradient(to top, #4c2289, #dad0fa)">
    <q-card square class="shadow-24 bg-secondary">
      <q-card-section class="bg-primary">
        <h4 class="text-center text-h5 text-white q-my-md">
          Envie uma inferência
        </h4>
      </q-card-section>
      <q-form class="q-px-sm q-pt-xl">
        <q-select
          label-color="black"
          v-model="model"
          :options="options"
          :option-label="'name'"
          label="Modelo"
        >
          <template v-slot:prepend>
            <q-icon name="api" color="accent" />
          </template>
        </q-select>
        <q-input
          square
          v-model="age"
          type="number"
          rules="[val>0]"
          label="Idade"
          label-color="black"
        >
          <template v-slot:prepend>
            <q-icon name="face_retouching_natural" color="accent" />
          </template>
        </q-input>
        <q-input
          square
          v-model="breathlessness_level"
          type="number"
          label="Nível de falta de ar"
          label-color="black"
        >
          <template v-slot:prepend>
            <q-icon name="air" color="accent" />
          </template>
        </q-input>
        <div class="text-center q-py-xl">
          <q-uploader model="uploaded_file" style="margin:auto;"/>
        </div>

      </q-form>
      <q-card-actions class="q-px-lg">
        <q-btn
          unelevated
          size="lg"
          color="primary"
          @click="submit"
          class="full-width text-white"
          label="Enviar"
        />
      </q-card-actions>
    </q-card>
  </q-page>
</template>

<style>
.q-card {
  width: 22.5rem;
  width: 80%;
  max-width: 400px;
  height: 750px;
}
</style>

<script>
import { ref } from 'vue'
const options = [
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
      model: ref(null),
      age: ref(null),
      breathlessness_level: ref(null),
      uploaded_file: ref(null),
      options,
    };
  },
};
</script>
