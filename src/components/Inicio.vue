<template>
  <div class="container" :style="cssProps">
    <b-container>
      <b-row>
        <b-col></b-col>
        <b-col cols="6">
          <BarraNavegacion />
          <v-card class="pa-5 mx-auto">
            <form>
              <v-text-field
                v-model="Restaurante"
                label="Restaurante o Comida"
                color="black"
                outlined
                dense
              >
                <v-icon slot="prepend" color="#FF4B4B">mdi-store</v-icon>
              </v-text-field>
              <v-text-field
                v-model="Ubicacion"
                label="Ubicación"
                color="black"
                outlined
                dense
              >
                <v-icon slot="prepend" color="#FF4B4B">mdi-map-marker</v-icon>
              </v-text-field>
              <router-link to="/Principal">
                <v-btn class="mr-4" color="#FF4B4B" elevation="2" block dark>
                  Buscar
                </v-btn>
              </router-link>
            </form>
          </v-card>
        </b-col>
        <b-col></b-col>
      </b-row>
    </b-container>
  </div>
</template>
<script>
import BarraNavegacion from "./barraNavegacion/BarraNavegacion";
export default {
  components: {
    BarraNavegacion,
  },
  data() {
    return {
      cssProps: {
        backgroundImage: `url(${require("@/assets/datafood_imagen_principal.jpg")})`,
      },
    };
  },
  methods: {},
};
</script>
<style scoped>
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
  background-position: center;
}
.container,
.container-sm,
.container-md,
.container-lg,
.container-xl {
  max-width: 1350px;
}
</style>