<style>
@import '/src/css/styles/sendInference.css';
</style>

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



<script>
import { ref } from 'vue'
import { api } from '/src/boot/axios'

export default {
  setup() {
    return {
      model: ref(null),
      age: ref(null),
      breathlessness_level: ref(null),
      uploaded_file: ref(null),
      options: ref([]),
    };
  },
  mounted () {
    api
      .get('/v1/models')
      .then(response =>{this.options=response.data.models})
  }
};
</script>
