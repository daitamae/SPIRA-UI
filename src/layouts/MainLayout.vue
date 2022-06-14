<template>
  <q-layout view="hHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn flat @click="drawer = !drawer" round dense icon="menu" />
        <q-toolbar-title>SPIRA Inference App</q-toolbar-title>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="drawer"
      show-if-above
      :mini="!drawer || miniState"
      @click.capture="drawerClick"
      :width="300"
      :breakpoint="500"
      bordered
      class="bg-secondary"
    >
      <q-scroll-area class="fit">
        <q-list padding>
          <q-item-label header> Menu </q-item-label>

          <EssentialLink
            v-for="link in essentialLinks"
            :key="link.title"
            v-bind="link"
          />
        </q-list>
      </q-scroll-area>
      <div class="q-mini-drawer-hide absolute" style="top: 15px; right: -17px">
        <q-btn
          dense
          round
          unelevated
          color="accent"
          icon="chevron_left"
          @click="miniState = true"
        />
      </div>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from "vue";
import EssentialLink from "components/EssentialLink.vue";

const linksList = [
  {
    title: "Home",
    icon: "home",
    to: "/",
  },
  {
    title: "Inferência",
    caption: "Crie uma nova inferência",
    icon: "publish",
    to: "/create_inference",
  },
  {
    title: "Histórico de Inferências",
    caption: "Inferências anteriores",
    icon: "view_list",
    to: "/inferences",
  },
  {
    title: "Modelos",
    caption: "Consulte os modelos disponíveis",
    icon: "api",
    to: "/models",
  },
  {
    title: "Suporte",
    caption: "Reporte um problema",
    icon: "help",
    to: "/help",
  },
  {
    title: "Sobre o SPIRA",
    icon: "info",
    link: "https://spira.ime.usp.br/coleta/",
  },
  {
    title: "Sair",
    icon: "logout",
    to: "/signin",
  },
];

export default defineComponent({
  name: "MainLayout",

  components: {
    EssentialLink,
  },

  setup() {
    const leftDrawerOpen = ref(false);
    const miniState = ref(false);

    return {
      essentialLinks: linksList,
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value;
      },
      drawer: ref(false),
      miniState,
      drawerClick(e) {
        // if in "mini" state and user
        // click on drawer, we switch it to "normal" mode
        if (miniState.value) {
          miniState.value = false;

          // notice we have registered an event with capture flag;
          // we need to stop further propagation as this click is
          // intended for switching drawer to "normal" mode only
          e.stopPropagation();
        }
      },
    };
  },
});
</script>
