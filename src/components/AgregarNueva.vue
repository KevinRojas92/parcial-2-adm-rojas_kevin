<template>

<button class="separacion_contenedores" @click="agregarNueva">Agregar nueva factura</button>

</template>
    
<script>
export default {
    name: 'AgregarNueva',
    
    props: {
        
    },

    data: function () {
        return {
            modal: false,
            sueldoTotal: 0,
            porcentajeSueldoU1: 0,
            porcentajeSueldoU2: 0
        }
    },

    methods: {
        agregarNueva () {
            if (localStorage.length > 0) {
                this.sueldosLocal = JSON.parse(localStorage.getItem("sueldos"));
    
                this.sueldoU1 = this.sueldosLocal.sueldoU1;
                this.sueldoU2 = this.sueldosLocal.sueldoU2;

                this.cambiarModal();

                this.calcularPorcentajes( this.sueldoU1,  this.sueldoU2);
            } else {
                alert("Recuerda que antes de agregar una nueva factura debes ingresar los sueldos de cada usuario");
                console.log("no hay datos");
            }
        },

        calcularPorcentajes (sueldoU1, sueldoU2) {
            this.sueldoTotal = parseFloat(sueldoU1) + parseFloat(sueldoU2);

            this.porcentajeSueldoU1 = (parseFloat(sueldoU1) * 100) / this.sueldoTotal;

            this.porcentajeSueldoU2 = (parseFloat(sueldoU2) * 100) / this.sueldoTotal;

            localStorage.setItem("porcentajeSueldoU1", JSON.stringify(this.porcentajeSueldoU1));

            localStorage.setItem("porcentajeSueldoU2", JSON.stringify(this.porcentajeSueldoU2));
        },

        cambiarModal () {
            this.modal = true;
            this.$emit("mostrar-modal", this.modal);
        }
    }
}
</script>