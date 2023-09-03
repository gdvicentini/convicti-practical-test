<template>
  <q-layout view="lHh Lpr lFf">
    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
      class="bg-primary"
    >
      <q-scroll-area
        style="
          height: calc(100% - 150px);
          margin-top: 150px;
          border-right: 1px solid #ddd;
        "
      >
        <q-list padding>
          <q-item clickable class="q-items-center">
            <div class="col">
              <div class="q-pl-md text-grey text-font-config">Menu</div>
              <div class="q-pa-md">
                <q-btn
                  label="Empresas"
                  color="white"
                  text-color="black"
                  icon="domain"
                  style="width: 230px"
                />
              </div>
            </div>
          </q-item>

          <q-item clickable v-ripple class="absolute-bottom" @click="logoff">
            <q-item-section avatar>
              <q-icon class="text-grey" name="power_settings_new" />
            </q-item-section>

            <q-item-section class="text-grey text-font-config">
              Sair
            </q-item-section>
          </q-item>
        </q-list>
      </q-scroll-area>

      <q-img
        class="absolute-top"
        src="../assets/navbar-footer-logo-convicti.png"
        style="width: 200px; margin: 25px auto"
      />
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from "vue";
// import EssentialLink from "components/EssentialLink.vue";

const linksList = [
  {
    title: "Docs",
    caption: "quasar.dev",
    icon: "school",
    link: "https://quasar.dev",
  },
  {
    title: "Github",
    caption: "github.com/quasarframework",
    icon: "code",
    link: "https://github.com/quasarframework",
  },
  {
    title: "Discord Chat Channel",
    caption: "chat.quasar.dev",
    icon: "chat",
    link: "https://chat.quasar.dev",
  },
  {
    title: "Forum",
    caption: "forum.quasar.dev",
    icon: "record_voice_over",
    link: "https://forum.quasar.dev",
  },
  {
    title: "Twitter",
    caption: "@quasarframework",
    icon: "rss_feed",
    link: "https://twitter.quasar.dev",
  },
  {
    title: "Facebook",
    caption: "@QuasarFramework",
    icon: "public",
    link: "https://facebook.quasar.dev",
  },
  {
    title: "Quasar Awesome",
    caption: "Community Quasar projects",
    icon: "favorite",
    link: "https://awesome.quasar.dev",
  },
];

export default defineComponent({
  name: "MainLayout",

  components: {
    // EssentialLink,
  },

  setup() {
    const leftDrawerOpen = ref(false);

    return {
      essentialLinks: linksList,
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value;
      },
    };
  },

  methods: {
    logoff() {
      localStorage.removeItem("user");
      this.$router.push("/login");
    },
  },
});
</script>

<style>
.text-font-config {
  font-family: "Nunito Sans", sans-serif;
  font-size: 16px;
  font-weight: 400;
  color: #000;
}
</style>
