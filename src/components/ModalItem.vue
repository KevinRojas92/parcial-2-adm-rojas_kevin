<template>

<div v-if="modal == true">
    <div>
        <div>
            <h3>Agrega una factura</h3>
            <a href="" @click="cerrar">x</a>
        </div>
    
        <form action="">
            <div>
                <label for="motivo">Motivo</label>
                <input id="motivo" type="text" name="motivo" placeholder="Motivo" v-model="motivo" @change="validacionMotivo">
            </div>
        
            <div style="margin-top: 25px;">
                <label for="valor">Valor</label>
                <input id="valor" type="number" name="valor" placeholder="Valor" v-model="valor">
            </div>
        </form>
    
        <button @click="agregar">Agregar</button>
    </div>

    <AgregarNueva/>
</div>

<div v-else>
    <AgregarNueva @mostrar-modal="mostrarModal"/>
</div>

</template>

<script>
import AgregarNueva from './AgregarNueva.vue';

export default {
    name: 'ModalItem',

    props: {

    },

    data: function () {
        return {
            modal: false,

            motivo: "",
            valor: "",

            factura: {},

            allFacturas: []
        }
    },

    components: {
        AgregarNueva
    },

    methods: {
        cerrar () {
            this.modal= false;
        },

        validacionMotivo () {
            if (!isNaN(this.motivo)) {
                alert("Estás ingresando un número. Por favor ingresa el motivo de esta factura");

                this.motivo = "";
            }
        },

        agregar () {
            if (this.motivo == "" || this.valor == "") {
                if (this.motivo == "" && this.valor == "") {
                    alert("Por favor ingresa un motvio y un valor para esta factura");
                } else if (this.motivo == "") {
                    alert("Por favor ingresa un motvio para esta factura");
                } else if (this.valor == "") {
                    alert("Por favor ingresa un valor para esta factura");
                }
            } else {
                this.factura.razon = this.motivo;
                this.factura.precio = parseFloat(this.valor);
                // this.factura.precioUsuario1 = ((this.factura.precio * porcentajeSueldoU1) / 100).toFixed(2);
                // this.factura.precioUsuario2 = ((this.factura.precio * porcentajeSueldoU2) / 100).toFixed(2);

                this.allFacturas.push(this.factura);

                this.factura = {};

                console.log(this.allFacturas);

                localStorage.setItem("facturas", JSON.stringify(this.allFacturas));
                this.cerrar ();
            }
        },

        mostrarModal (modal) {
            this.modal = modal;
        }
    }
}
</script>