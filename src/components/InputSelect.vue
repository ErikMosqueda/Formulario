<script>
export default {
    
    data() {
        return {
            dato: '',
        }
    },
    methods: {
        enviar() {
            dato: this.info,
            this.$emit('informacionSelect',this.dato)
        }
    }
}
</script>

<template>
    <div>
        <slot></slot> ({{ dato}})
        <br>
        <select name="info" id="info" v-model="dato">
            <option value="1">Soltero</option>
            <option value="2">Casado</option>
            <option value="3">Divorciado</option>
            <option value="4">Separado</option>
            <option value="5">Union libre</option>
            <option value="6">Viudo</option>
            </select>

    </div>
</template>