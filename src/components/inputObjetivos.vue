<script>
export default {
    
    data() {
        return {
            dato: "",
        }
    },
    props:{index:null},
    methods: {
        enviar() {
            dato: this.info,
            this.$emit('informacion',this.dato, this.index)
        }
    }
}
</script>

<template>
    <div>
        <slot></slot>
        <input type="text" v-model="dato" name="info" id="info" @input="enviar"
        class="px-2 py-1 rounded-lg mb-3 ml-2 mr-2">
    </div>
</template>