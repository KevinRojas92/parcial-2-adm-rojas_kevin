<template>

<div>
    <div>
        <div class="separacion_contenedores organizador_res">
            <h2 class="separacion_contenedores">Mis facturas:</h2>

            <p style="margin-top: 20px;" v-if="copiaArrayFacturas.length == 0">Aún no has agregado facturas.</p>

            <div class="resultado_individual" v-for="(i, index) in copiaArrayFacturas" :key="index">
                <div class="header_resultado">
                    <h3>{{i.razon}}</h3>
                    <button @click="borrar(index)">x</button>
                </div>
    
                <div class="resultados" style="margin-top: 25px;">
                    <p>Usuario 1</p>
                    <p>${{i.precioUsuario1}}</p>
                </div>
    
                <div class="resultados" style="margin-top: 20px;">
                    <p>Usuario 2</p>
                    <p>${{i.precioUsuario2}}</p>
                </div>
    
                <div class="resultado_total">
                    <p>Total</p>
                    <p>{{i.precio}}</p>
                </div>
            </div>
        </div>
    </div>
 </div>
    
</template>
    
<script>
export default {
    name: 'ResultadosItems',

    props: {
        arrayFacturas: Array
    },

    data: function () {
        return {
            facturasStorage: JSON.parse(localStorage.getItem("facturas")),

            copiaArrayFacturas: this.arrayFacturas
        }
    },

    mounted () {
        if (this.facturasStorage == null) {
            console.log("No hay datos en LocalStorage");
        } else {
            this.copiaArrayFacturas = [];

            this.facturasStorage.forEach(element => {
                this.copiaArrayFacturas.push(element);
            });
        }
    },

    methods: {
        borrar (index) {
            this.copiaArrayFacturas.splice(index, 1);

            localStorage.removeItem("facturas");

            if (this.copiaArrayFacturas.length > 0) {
                localStorage.setItem("facturas", JSON.stringify(this.copiaArrayFacturas));
            }
        }
    }
}
</script>