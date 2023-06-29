<template>

<div>
    <div>
        <div>
            <h3>Agrega una factura</h3>
            <a href="">x</a>
        </div>
    
        <form action="">
            <div>
                <label for="motivo">Motivo</label>
                <input id="motivo" type="text" name="motivo" placeholder="Motivo">
            </div>
        
            <div style="margin-top: 25px;">
                <label for="valor">Valor</label>
                <input id="valor" type="number" name="valor" placeholder="Valor">
            </div>
        </form>
    
        <button>Agregar</button>
    </div>
</div>

</template>

<script>
export default {
  name: 'ModalItem',
  props: {
  }
}
</script>