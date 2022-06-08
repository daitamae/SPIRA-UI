<template>
  <q-page class="window-height window-width row justify-center items-center">
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
          label="Modelo"
        >
          <template v-slot:prepend>
            <q-icon name="api" color="accent" />
          </template>
        </q-select>
        <q-input
          square
          clearable
          v-model="number"
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
          clearable
          v-model="number"
          type="number"
          label="Nível de falta de ar"
          label-color="black"
        >
          <template v-slot:prepend>
            <q-icon name="air" color="accent" />
          </template>
        </q-input>
        <q-uploader square class="q-px-sm vertical-middle" />
      </q-form>
      <q-card-actions class="q-px-lg q-pt-xl">
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
