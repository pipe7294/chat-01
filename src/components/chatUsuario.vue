<template>
    <div class="chat-box">
        <div v-for="(mensaje, i) in mensajes" :key="i" 
        :class="{izquierda: mensaje.id == 0, derecha: mensaje.id == 1}">
            <p>{{ mensaje.nombre }}</p>
            <p :style= "{backgroundColor: mensaje.color}">{{ mensaje.textoMensaje }}</p>
        </div>
    </div>
</template>

<script>

export default {
    props:["mensajes"],
}

</script>

<style>

.izquierda {
    align-self: flex-start;
    text-align: left;
    align-items: flex-start;
}
.derecha {
    align-self: flex-start;
    text-align: right;
    align-items: flex-start;
}

</style>