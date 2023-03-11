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
            this.$emit('informacionTextArea',this.dato)
        }
    }
}
</script>

<template>
    <div>
        <slot></slot> ({{ dato}})
        <br>
            <textarea type="text" name="info" id="info" v-model="dato" class="px-2 py-1 rounded-lg mb-3 ml-2 mt-2"
            rows="5" cols="50" @input="enviar">
            </textarea>

    </div>
</template>