<template>

<div id="app">
  <ModalItem/>

  <SueldoUsuarios/>

  <ResultadosItems/>
</div>

</template>

<script>

import ModalItem from './components/ModalItem.vue'
import SueldoUsuarios from './components/SueldoUsuarios.vue'
import ResultadosItems from './components/ResultadosItems.vue'

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
    ModalItem,
    SueldoUsuarios,
    ResultadosItems
  }
}
</script>
