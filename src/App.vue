<template>

  <div id="app">
    <SueldoUsuarios/>
  
    <ModalItem/>
  </div>
  
</template>
  
<script>
  
  import SueldoUsuarios from './components/SueldoUsuarios.vue';
  import ModalItem from './components/ModalItem.vue';
  
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
      ModalItem
    }
  }
</script>