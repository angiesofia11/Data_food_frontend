<template>
  <div>
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
    <iframe
      width="1350"
      height="636"
      src="https://app.powerbi.com/view?r=eyJrIjoiZWQxNmU0ZGEtZDYyNy00MjEzLThkNDgtNmEzMWUwMGFlNTFiIiwidCI6ImFlNmNhODZjLWU1NTktNDUxNi04ZTM2LWY4OTk2ZjQ1MjliMCIsImMiOjR9"
      frameborder="0"
      allowFullScreen="true"
    ></iframe>
  </div>
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
};
</script>
<style scoped>
</style>