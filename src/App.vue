<template>

<div id="app">
  <SueldoUsuarios/>

  <ModalItem/>

  <ResultadosItems/>
</div>

</template>

<script>

import SueldoUsuarios from './components/SueldoUsuarios.vue';
import ModalItem from './components/ModalItem.vue';
import ResultadosItems from './components/ResultadosItems.vue';

export default {
  name: 'App',

  data: function () {
    return {
      sueldoU1: "",
      sueldoU2: "",

      modal: false,

      motivo: "",
      valor: "",

      factura: {},

      allFacturas: []
    }
  },

  components: {
    SueldoUsuarios,
    ModalItem,
    ResultadosItems
  }
}
</script>
