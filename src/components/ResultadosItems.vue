<template>

<div>
    <div>
        <div class="separacion_contenedores organizador_res">
            <h2 class="separacion_contenedores">Mis facturas:</h2>

            <p style="margin-top: 20px;" v-if="arrayFacturas.length == 0">Aún no has agregado facturas.</p>

            <div class="resultado_individual" v-for="(i, index) in arrayFacturas">
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
        arrayFacturas: []
    },

    data: function () {
        return {
            facturasStorage: JSON.parse(localStorage.getItem("facturas"))
        }
    },

    mounted () {
        if (this.facturasStorage.length > 0) {
            this.facturasStorage.forEach(element => {
                this.arrayFacturas.push(element);
            });
        } else {
            console.log("No hay datos en LocalStorage");
        }
    },

    methods: {
        borrar (index) {
            this.arrayFacturas.splice(index, 1);

            localStorage.removeItem("facturas");

            if (this.arrayFacturas.length > 0) {
                localStorage.setItem("facturas", JSON.stringify(this.arrayFacturas));
            }
        }
    }
}
</script>