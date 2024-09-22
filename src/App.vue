<template>
  <!-- <h1 v-bind:style="miColor"> or <h1 :style="miColor"> for red text-->
  <h1 :class="selector">
    Hola me llamo {{ miNombre }} y tendre {{ miEdad+1 }}
  </h1>
  <!-- <button v-on:click="saludar(nombre)">Aceptar</button> -->
  <button @click="saludar(miNombre)">Aceptar</button>

  <br>
  <br>

  <!-- Variables reactivas (requieren cambio en pantalla) -->
   <button @click="decremento">-</button>
    <span :class="miColor">{{ contador }}</span>
   <button @click="incremento">+</button>
   <div v-if="contador<0"> Es menor que 0</div>
   <div v-else-if="contador>0"> Es mayor de 0</div>

   <!-- Componente que aparece o no aparece -->
    <div v-show="comprobacion">No esta permitido el 0</div>

</template>


<script setup>
  const miNombre = "Andres";
  const miEdad = 29;
  const selector = "amGreen";
  const saludar = (nombre) => {
    alert(`Hola ${nombre}`)
  }
  
  // Variables reactivas
  import { ref, computed } from "vue";
  const miColor = ref("azul");
  const contador = ref(0);
  const decremento = () => {
    contador.value--;
    if (contador.value < 0) {
      miColor.value = "rojo"
    }
  };

  const incremento = () => {
    contador.value++;
    if (contador.value > 0) {
      miColor.value = "amGreen"
    }
  };

  // Propiedad computada
  const comprobacion=computed (()=>{
    return contador.value===0;
  })

</script>


<style scoped>
  .amGreen{
    color: #0A7968;
  }

  span {
    padding: 0 5px;
  }

  .rojo {
    color: red;
  }

  .azul{
    color: blue;
  }

</style>