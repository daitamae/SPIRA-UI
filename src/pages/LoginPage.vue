<template>
  <q-page
    class="window-height window-width row justify-center items-center"
    style="background: linear-gradient(to top, #4c2289, #dad0fa)"
  >
    <q-card square class="shadow-24">
      <q-card-section class="bg-primary">
        <img
          alt="SPIRA logo"
          src="~assets/spira_white.svg"
          style="width: 200px"
        />
      </q-card-section>
      <q-form class="q-px-sm q-pt-xl">
        <q-input
          v-model="username"
          square
          clearable
          type="username"
          label="Usuário"
          class="q-px-sm q-pt-sm"
        >
          <template v-slot:prepend>
            <q-icon name="person" color="accent" />
          </template>
        </q-input>
        <q-input
          v-model="password"
          square
          clearable
          type="password"
          label="Senha"
          class="q-px-sm q-pt-sm"
        >
          <template v-slot:prepend>
            <q-icon name="lock" color="accent" />
          </template>
        </q-input>
      </q-form>
      <q-card-actions class="q-px-lg q-pt-xl">
        <q-btn
          unelevated
          size="lg"
          color="primary"
          class="full-width text-white"
          label="Entrar"
        />
      </q-card-actions>
      <q-card-section class="text-center q-pa-sm">
        <a href="" class="text-grey-6">Esqueceu a senha?</a>
      </q-card-section>
    </q-card>
  </q-page>
</template>

<style>
.q-card {
  width: 22.5rem;
  width: 80%;
  max-width: 400px;
  height: 540px;
}
</style>

<script>
import { ref } from 'vue'

export default {
  setup() {
    return {
      username: ref(null),
      password: ref(null),
    };
  },
};
</script>
