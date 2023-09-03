<template>
  <q-page class="q-pa-md bg-grey-3">
    <div class="q-pa-md q-gutter-md row config-header">
      <div class="col">
        <q-input
          v-model="searchQuery"
          placeholder="Pesquisar"
          dense
          outlined
          clearable
          class="float-left search-bar"
          bg-color="white"
        >
          <template v-slot:prepend>
            <q-icon name="search" />
          </template>
        </q-input>
      </div>

      <div class="col">
        <q-btn
          outline
          icon-right="add"
          label="Adicionar Empresa"
          color="secondary"
          @click="adicionarEmpresa"
          class="float-right"
        />
      </div>

      <q-dialog
        v-model="showCompanyForms"
        position="right"
        :class="{ 'menu-lateral-dialog': showCompanyForms }"
      >
        <div>
          <company-forms-component :confirm="setListCompayForms" />
        </div>
      </q-dialog>

      <!-- <q-page-sticky
        v-if="showCompanyForms"
        position="right"
        :style="{ width: '400px', height: '100%' }"
      >
        <company-forms-component :confirm="setListCompanyForms" />
      </q-page-sticky> -->
    </div>

    <!-- Área do Mapa -->
    <div class="map-container">
      <div id="map" class="map-element"></div>
    </div>
  </q-page>
</template>

<script>
import { defineComponent, ref } from "vue";
import CompanyFormsComponent from "../components/CompanyFormsComponent.vue";
import "ol/ol.css";
import Map from "ol/Map.js";
import View from "ol/View";
import TileLayer from "ol/layer/Tile";
import OSM from "ol/source/OSM";

export default defineComponent({
  name: "IndexPage",
  components: {
    CompanyFormsComponent,
  },
  setup() {
    let map = null;
    const searchQuery = ref("");
    const showCompanyForms = ref(false);
    const company = ref("");

    return {
      searchQuery,
      map,
      showCompanyForms,
      company,
    };
  },

  mounted() {
    this.map = new Map({
      target: "map",
      layers: [
        new TileLayer({
          source: new OSM(),
        }),
      ],
      view: new View({
        center: [0, 0],
        zoom: 2,
      }),
    });
  },

  methods: {
    adicionarEmpresa() {
      this.showCompanyForms = true;
    },
    setListCompayForms(list) {
      this.company = list;
    },
  },
});
</script>

<style>
.search-bar {
  min-width: 400px;
  max-width: 600px;
  height: 70px;
}
.config-header {
  height: 100px;
}
.menu-right {
  width: 400px;
  height: 100%;
  position: absolute;
  top: 0;
  right: 0;
  margin: 0;
}
.map-container {
  clear: both;
  position: relative;
  height: calc(100vh - 150px);
  border-radius: 50px;
}
.map-element {
  position: absolute;
  width: 100%;
  height: 100%;
}
</style>
