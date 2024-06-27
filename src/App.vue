<template>
  <div id="app">
    <!-- primer usuario  -->
    <div class="usuario">
      <img :src="usuario1.foto" alt="foto usuario 1">
      <span>{{ usuario1.nombre }}</span>
      <input v-model="usuario1.color" type="color">
      <textarea v-model="usuario1.textoMensaje" name="" id=""></textarea>
      <button @click="enviarMensaje(usuario1)">Enviar</button>
    </div>


    <!-- segundo usuario  -->
    <div class="usuario">
      <img :src="usuario2.foto" alt="foto usuario 2">
      <span>{{ usuario2.nombre }}</span>
      <input v-model="usuario2.color" type="color">
      <textarea v-model="usuario2.textoMensaje" name="" id=""></textarea>
      <button @click="enviarMensaje(usuario2)">Enviar</button>
    </div>
  </div>

</template>

<script>
import axios from 'axios';
import chatUsuario from './components/chatUsuario.vue'

export default {
  name: 'App',
  components: {
    chatUsuario,
  },
  data(){
    return {
      usuario1:{
        nombre:"",
        foto:"",
        textoMensaje:"",
        color:"00FF00",
        id:"0",
      },
      usuario2:{
        nombre:"",
        foto:"",
        textoMensaje:"",
        color:"D0FF00",
        id:"1",
      },
      mensajesUsuarios:"",
    }
  },
  methods: {
    enviarMensaje(usuario){
      this.mensajesUsuarios.push({...usuario})
    }

  },
  async mounted(){
    const url ="https://randomuser.me/api?results=2";
    const {data} = await axios.get(url);

    // usuario 1
    this.usuario1.nombre = data.results[0].name.first;
    this.usuario1.foto = data.results[0].picture.large;

    // usuario 2
    this.usuario2.nombre = data.results[1].name.first;
    this.usuario2.foto = data.results[1].picture.large;
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.usuario{
  display: flex;
  flex-direction: column;
}

input {
  width: 100%;
}
</style>
