<template>
  <b-container class="container mx-auto">
    <b-row>
      <b-col> </b-col>
      <b-col cols="5">
        <v-card class="pa-5 mx-auto" min-width="400">
          <div>
            <b-tabs content-class="mt-3" align="center">
              <b-tab title="Usuario" active>
                <form @submit.prevent="submit">
                  <div class="mt-6">
                    <v-btn class="my-3" block elevation="1" plain
                      >Inicia sesión con Google</v-btn
                    >
                    <v-btn block elevation="1" plain
                      >Inicia sesión con Facebook</v-btn
                    >
                  </div>
                  <div class="linea mt-4">
                    <b-row class="mt-4">
                      <b-col sm="2">
                        <v-icon slot="prepend" color="#FF4B4B">mdi-mail</v-icon>
                      </b-col>
                      <b-col sm="10">
                        <b-form-input
                          v-model="emailLogin"
                          type="email"
                          placeholder="Correo"
                        ></b-form-input>
                      </b-col>
                    </b-row>
                    <b-row class="mt-3">
                      <b-col sm="2">
                        <v-icon slot="prepend" color="#FF4B4B">mdi-key</v-icon>
                      </b-col>
                      <b-col sm="10">
                        <b-form-input
                          type="password"
                          v-model="passwordLogin"
                          aria-describedby="password-help-block"
                          placeholder="Contraseña"
                        ></b-form-input>
                        <div class="mt-2 text-right">
                          <router-link to=""
                            ><b-link>Olvidé mi contraseña</b-link></router-link
                          >
                        </div>
                      </b-col>
                    </b-row>
                  </div>
                  <div class="mt-2">
                    <v-btn
                      class="mr-4"
                      color="#FF4B4B"
                      elevation="2"
                      block
                      dark
                      @click="loginUser"
                    >
                      Iniciar Sesión
                    </v-btn>
                  </div>
                  <div class="mt-2 text-center">
                    <router-link to="/LinksRegistros"
                      ><p>Registrarme</p></router-link
                    >
                  </div>
                </form></b-tab
              >
              <b-tab title="Empresa">
                <form @submit.prevent="submit">
                  <div class="mt-6">
                    <v-btn class="my-3" block elevation="1" plain
                      >Inicia sesión con Google</v-btn
                    >
                    <v-btn block elevation="1" plain
                      >Inicia sesión con Facebooke</v-btn
                    >
                  </div>
                  <div class="linea mt-4">
                    <b-row class="mt-4">
                      <b-col sm="2">
                        <v-icon slot="prepend" color="#FF4B4B">mdi-mail</v-icon>
                      </b-col>
                      <b-col sm="10">
                        <b-form-input
                          v-model="emailLoginEmpresa"
                          type="email"
                          placeholder="Correo"
                        ></b-form-input>
                      </b-col>
                    </b-row>
                    <b-row class="mt-3">
                      <b-col sm="2">
                        <v-icon slot="prepend" color="#FF4B4B">mdi-key</v-icon>
                      </b-col>
                      <b-col sm="10">
                        <b-form-input
                          type="password"
                          v-model="passwordLoginEmpresa"
                          aria-describedby="password-help-block"
                          placeholder="Contraseña"
                        ></b-form-input>
                        <div class="mt-2 text-right">
                          <router-link to=""
                            ><b-link>Olvidé mi contraseña</b-link></router-link
                          >
                        </div>
                      </b-col>
                    </b-row>
                  </div>
                  <div class="mt-2">
                    <v-btn
                      class="mr-4"
                      color="#FF4B4B"
                      elevation="2"
                      block
                      dark
                      @click="loginUserEmpresa"
                    >
                      Iniciar Sesión
                    </v-btn>
                  </div>
                  <div class="mt-2 text-center">
                    <router-link to="/LinksRegistros"
                      ><p>Registrarme</p></router-link
                    >
                  </div>
                </form>
              </b-tab>
            </b-tabs>
          </div>
        </v-card>
        <v-alert
          class="mt-7 text-center"
          v-if="alertaLogin === true"
          border="top"
          color="#FF4B4B"
          colored-border
          type="error"
          elevation="2"
        >
          Inicio de sesión no exitoso. Por favor intentelo de nuevo
        </v-alert>
      </b-col>
      <b-col></b-col>
    </b-row>
  </b-container>
</template>
<script>
import axios from "axios";

export default {
  data() {
    return {
      alertaLogin: false,
      emailLogin: "",
      passwordLogin: "",
      emailLoginEmpresa: "",
      passwordLoginEmpresa: "",
    };
  },
  methods: {
    loginUser() {
      let json = {
        email: this.emailLogin,
        password: this.passwordLogin,
      };
      axios
        .post("https://datafood.herokuapp.com/api/usuario/login", json)
        .then((response) => {
          this.alertaLogin = false;
          const token = response.statusText;
          localStorage.setItem("jwt", token);
          console.log(response);
          this.$router.push("./Principal");
        })
        .catch((error) => {
          this.alertaLogin = true;
          console.log(error);
        });
    },
    loginUserEmpresa() {
      let json = {
        correo: this.emailLoginEmpresa,
        pws: this.passwordLoginEmpresa,
      };
      axios
        .post("https://datafood.herokuapp.com/api/empresa/login", json)
        .then((response) => {
          this.alertaLogin = false;
          const token = response.statusText;
          localStorage.setItem("jwt", token);
          console.log(response);
          this.$router.push("./Principal");
        })
        .catch((error) => {
          this.alertaLogin = true;
          console.log(error);
        });
    },
  },
};
</script>
<style>
a:hover {
  color: #dc3545;
  text-decoration: underline;
}
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
}
.v-application a {
  color: #41c5d3;
}
</style>