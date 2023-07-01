<template>

<div>
    <div>
        <div>
            <h2>Mis facturas:</h2>

            <p style="margin-top: 20px;" v-if="!facturasStorage">Aún no has agregado facturas.</p>

            <div v-for="i in facturasStorage">
                <div>
                    <h3>{{i.razon}}</h3>
                    <button>x</button>
                </div>
    
                <div style="margin-top: 25px;">
                    <p>Usuario 1</p>
                    <p>${{i.precioUsuario1}}</p>
                </div>
    
                <div style="margin-top: 20px;">
                    <p>Usuario 2</p>
                    <p>${{i.precioUsuario2}}</p>
                </div>
    
                <div>
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
        
    },

    data: function () {
        return {
            facturasStorage: JSON.parse(localStorage.getItem("facturas"))
        }
    },
}
</script>