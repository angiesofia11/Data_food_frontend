<template>
  <b-container>
    <BarraNavegacion />
    <v-btn
      class="mt-5 mx-7"
      color="#FF4B4B"
      elevation="2"
      fab
      icon
      small
      to="/Estadisticas"
      ><v-icon>mdi-arrow-left</v-icon></v-btn
    >
    <b-card elevation="2">
      <a
        href="https://plotly.com/~Lugares/5/?share_key=PJajHfvMhhFDn7k5oztU2p"
        target="_blank"
        title="Plot 5"
        style="text-align: center"
        ><img
          src="https://plotly.com/~Lugares/5.png?share_key=PJajHfvMhhFDn7k5oztU2p"
          alt="Plot 5"
          style="max-width: 100%; width: 600px"
          width="600"
          onerror="this.onerror=null;this.src='https://plotly.com/404.png';"
      /></a>
    </b-card>
  </b-container>
</template>
<script>
import BarraNavegacion from "@/components/barraNavegacion/BarraNavegacion";
export default {
  components: {
    BarraNavegacion,
  },
  data() {
    return {};
  },
  methods: {},
};
</script>
<style scoped>
</style>