<template>
  <div class="config-page">
    <q-form v-model="submitCompany">
      <div class="q-pa-md">
        <subtitle-forms-component title="Cadastrar empresa" class="text-bold" />

        <div class="q-pa-md q-gutter-md row">
          <div class="col">
            <q-input outlined label="Nome" v-model="nome" />
          </div>
          <div class="col">
            <q-input outlined label="Observações" v-model="observacoes" />
          </div>
        </div>

        <div class="q-pa-md q-gutter-md row">
          <div class="col">
            <q-input outlined label="CNPJ" v-model="cnpj" />
          </div>
          <div class="col">
            <q-select
              outlined
              label="Categoria"
              v-model="categoria"
              :options="categorias"
            />
          </div>
        </div>

        <div class="q-pa-md">
          <q-input outlined label="Email" v-model="email" />
        </div>
        <div class="q-pa-md">
          <q-input outlined label="Whatsapp" v-model="whatsapp" />
        </div>
        <div class="q-pa-md">
          <q-input outlined label="Representante" v-model="representante" />
        </div>

        <div class="q-pa-md q-gutter-md row">
          <div class="col">
            <q-input outlined label="Latitude" v-model="latitude" />
          </div>
          <div class="col">
            <q-input outlined label="Longitude" v-model="longitude" />
          </div>
        </div>

        <div class="q-pa-md q-gutter-md row">
          <div class="col">
            <q-select
              outlined
              label="Estado"
              v-model="estado"
              :options="estados"
            />
          </div>
          <div class="col">
            <q-select
              outlined
              label="Cidade"
              v-model="cidade"
              :options="cidades"
            />
          </div>
        </div>

        <div class="q-pa-md q-gutter-md row">
          <div class="col">
            <q-btn
              label="Cancelar"
              color="grey-3"
              text-color="grey"
              style="width: 180px"
            />
          </div>
          <div class="col">
            <q-btn
              label="Cadastrar Empresa"
              color="primary"
              text-color="grey"
              type="submit"
            />
          </div>
        </div>
      </div>
    </q-form>
  </div>
</template>

<script>
import { defineComponent, ref } from "vue";
import SubtitleFormsComponent from "./titles/SubtitleFormsComponent.vue";

export default defineComponent({
  name: "CompanyFormsComponent",
  components: {
    SubtitleFormsComponent,
  },
  setup() {
    const nome = ref("");
    const observacoes = ref("");
    const cnpj = ref("");
    const categoria = ref("");
    const email = ref("");
    const whatsapp = ref("");
    const representante = ref("");
    const latitude = ref("");
    const longitude = ref("");
    const estado = ref("");
    const cidade = ref("");

    return {
      nome,
      observacoes,
      cnpj,
      categoria,
      email,
      whatsapp,
      representante,
      latitude,
      longitude,
      estado,
      cidade,
    };
  },
});
</script>

<style>
.config-page {
  height: 100%;
  background-color: #f5f5f5;
}
</style>
