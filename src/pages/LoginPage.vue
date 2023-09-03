<template>
  <q-page class="flex flex-center q-pa-sm bg-convicti">
    <div class="">
      <div class="flex flex-center q-pa-sm q-py-xl">
        <div class="">
          <q-img
            width="350px"
            src="../assets/navbar-footer-logo-convicti.png"
          />
        </div>
      </div>
      <q-form>
        <div>
          <div class="q-pa-md">
            <div class="text-login">E-mail</div>
            <q-input
              outlined
              :dense="dense"
              bg-color="white"
              v-model="login"
              class="config-labels"
            />
          </div>
          <div class="q-pa-md">
            <div class="text-login">Senha</div>
            <q-input
              outlined
              :dense="senha"
              bg-color="white"
              v-model="senha"
              class="config-labels"
            />
          </div>
          <div class="q-pa-md">
            <q-btn
              color="secondary"
              label="Entrar"
              @click="submitLogin"
              class="config-labels"
            />
          </div>
        </div>
      </q-form>
    </div>
  </q-page>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import { useRouter } from "vue-router";
// import axios from "axios";

export default defineComponent({
  name: "LoginPage",
  components: {},
  setup() {
    const login = ref("");
    const senha = ref("");
    const dense = ref(true);

    return {
      login,
      senha,
      dense,
    };
  },
  created() {
    const user = localStorage.getItem("user");
    // if (user) {
    //   this.user = user;
    //   this.remember = true;
    // }
  },
  methods: {
    submitLogin() {
      const router = useRouter();
      router.push("/");
    },
    // viewPassword() {
    //   this.type = !this.type;
    // },
    // async login() {
    // const tokenAuth = localStorage.getItem('token');
    // if (!tokenAuth) {
    //   const userController = new UserController();
    //   userController.authWithoutLS(
    //     {
    //       username: this.user,
    //       password: this.password,
    //     },
    //     this.remember,
    //     this
    //   );
    // } else {
    //   try {
    //     const response = await axios.post(
    //       `${process.env.API_URL}:${process.env.PORT}/login`,
    //       null,
    //       {
    //         headers: {
    //           'Access-Control-Allow-Origin': '*',
    //           Authorization: tokenAuth,
    //         },
    //       }
    //     );
    //     this.roles = response.data.role;
    //     this.integration_id = response.data.integration_id;
    //     console.log('Nível de usuario:', this.roles);
    //     console.log('integration ID:', this.integration_id);
    //   } catch (error) {
    //     console.error('Erro ao realizar o login:', error);
    //   }
    //   // const userController = new UserController();
    //   // userController.authWithLS(
    //   //   {
    //   //     username: this.user,
    //   //     password: this.password,
    //   //   },
    //   //   this.remember,
    //   //   this,
    //   //   this.roles, // Passar o nível de usuário para o método auth
    //   //   parseInt(this.integration_id) // Passar o integrationId para o método auth
    //   // );
  },
  // },
  // },
});
</script>

<style scoped lang="scss">
.text-login {
  font-size: 16px;
  font-weight: 500;
  font-family: "Nunito Sans", sans-serif;
  color: #fff;
}

.config-labels {
  width: 500px;
}

.bg-convicti {
  background: #0e044a;
}
</style>
