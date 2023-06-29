<template>

<button @click="agregarNueva">Agregar nueva factura</button>

</template>
    
<script>
export default {
    name: 'AgregarNueva',
    
    props: {
        
    },

    data: function () {
        return {
            modal: false
        }
    },

    methods: {
        // calcularPorcentajes () {
        //     sueldoTotal = parseFloat(this.sueldoU1) + parseFloat(this.sueldoU2);

        //     porcentajeSueldoU1 = (parseFloat(this.sueldoU1) * 100) / sueldoTotal;

        //     porcentajeSueldoU2 = (parseFloat(this.sueldoU2) * 100) / sueldoTotal;
        // },

        agregarNueva () {
            console.log('Se activo el boton de agregar');

            this.cambiarModal();
            // if (localStorage.length > 0) {
            //     this.sueldosLocal = JSON.parse(localStorage.getItem("sueldos"));
    
            //     this.sueldoU1 = this.sueldosLocal.sueldoU1;
            //     this.sueldoU2 = this.sueldosLocal.sueldoU2;

            //     this.cambiarModal();

            //     this.calcularPorcentajes();
            // } else {
            //     alert("Recuerda que antes de agregar una nueva factura debes ingresar los sueldos de cada usuario");
            //     console.log("no hay datos");
            // }
        },

        cambiarModal () {
            this.modal = true;
            this.$emit("mostrar-modal", this.modal);
        }
    }
}
</script>