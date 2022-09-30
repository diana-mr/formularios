<template>
  <div class="container mt-3">
  <Header />

  <formulario />
  </div>
</template>

<script>
  import Header from "./components/Header.vue";
  import Formulario from "./components/formulario.vue";

  export default {
    components: {
      Header,
      Formulario,
    }
  }
</script>
