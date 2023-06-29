<template>

<form action="">
    <div>
        <label for="usuario1">{{usuario1}}</label>
        <input id="usuario1" type="number" name="usuario1" :placeholder="sueldoU1" v-model="sueldoU1" @change="guardarSueldos">
    </div>
            
    <div style="margin-top: 25px;">
        <label for="usuario2">{{usuario2}}</label>
        <input id="usuario2" type="number" name="usuario2" :placeholder="sueldoU2" v-model="sueldoU2" @change="guardarSueldos">
    </div>
</form>
    
</template>
    
<script>
export default {
    name: 'SueldoUsuarios',

    props: {
    },

    data: function () {
        return {
            usuario1: 'Nombre Usuario 1',
            usuario2: 'Nombre Usuario 2',

            sueldoU1: "Sueldo Usuario 1",
            sueldoU2: "Sueldo Usuario 2",

            sueldos: {},

            sueldosLocal: {}
        }
    },

    mounted () {
        if (localStorage.length > 0) {
            this.sueldosLocal = JSON.parse(localStorage.getItem("sueldos"));

            this.sueldoU1 = this.sueldosLocal.sueldoU1;
            this.sueldoU2 = this.sueldosLocal.sueldoU2;
        } else {
            console.log("no hay datos");
        }
    },

    methods: {
        guardarSueldos () {
            console.log('Se llamo la funcion');

            let sueldoUsuario1 = this.sueldoU1;
            let sueldoUsuario2 = this.sueldoU2;

            if (sueldoUsuario1 != "Sueldo Usuario 1" || sueldoUsuario2 != "Sueldo Usuario 2") {
                console.log('entro al primer if');

                this.sueldos.sueldoU1 = this.sueldoU1;
                this.sueldos.sueldoU2 = this.sueldoU2;

                if (this.sueldos.sueldoU1 != "Sueldo Usuario 1" && this.sueldos.sueldoU2 != "Sueldo Usuario 2") {
                    localStorage.setItem("sueldos", JSON.stringify(this.sueldos));
                }
            }
        }
    }
}
</script>