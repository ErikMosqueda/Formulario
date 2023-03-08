<script>
export default {
    
    data() {
        return {
            dato: 'PRUEBA DE ENVIO dato',
        }
    },
    methods: {
        enviar() {
            dato: this.info,
            this.$emit('informacion',this.dato)
        }
    }
}
</script>

<template>
    <div>
        <slot></slot> ({{ dato}})
        <br>
        <input type="text" v-model="dato" name="info" id="info" class="px-2 py-1 rounded-lg mb-3 ml-2 mr-2" @input="enviar">

    </div>
</template>