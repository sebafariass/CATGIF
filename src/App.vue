<template>
  <div class="informacion">
    <div class="titulo">
      <h1> CREA TU GIF </h1>
    </div>

    <!-- filtro a seleccion -->
    <div class="Filtros">
      <!-- input title -->
      <p class="datos"> Ingresa texto:
        <input v-model="title"
               type="text"
               placeholder="Texto"/>
      </p>
     
         <!-- , usando directiva v-for, vinculamos datos al modelo
        --->
      <p class="datos">
        Filtro:
        <select v-model="filtro_seleccionado">
          <option disabled selected> Selecciona </option>
          
          <option
          
            @click="filtro_seleccionado = elemento"
            v-for="elemento in filtros"
            :key="elemento"
            :value="elemento" >
            {{ elemento }}
          </option>
        </select>
      </p>
      <!-- LETRA COLOUR  -->
      <div class="datos">
        <p class="color">
          Color Letra:
          <select v-model="color_seleccionado">
            <option disabled selected> Selecciona </option>
            <option
              @click="color_seleccionado = elemento"
              v-for="elemento in colores"
              :key="elemento"
              :value="elemento"
            >
              {{ elemento }}
            </option>
          </select>
        </p>
        <!-- muestra el color a incorporar en imagen -->
        <div
          :style="{ 'background-color': this.color_seleccionado }"
          class="circulo_color"
        ></div>
      </div>
      <!-- Tamaño letra -->
      <p class="datos">
        Tamaño Fuente:
        <input
          v-model.number="size"
          type="number"
          min="1"
        />
      </p>
    </div>
    <!-- Resultado a mostrar -->
    <div class="gif">
     
     <!--boton -->
      <button @click="mostrar_gato" class="mostrar_gato_boton"> Genera tu Gato Divertido! </button>
      <!-- gif imagen -->
      <div>
        <img v-if="image_fuente" :src="image_fuente" alt="Gato_Fail_Img_Try_Again" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  // Componente App
  name: "App",
  data() {
    return {
   
      title: "", //asigno propiedad title para guardar info de input,  USO DE STRING!!!
      filtros: ["blur", "mono", "sepia", "negative", "paint", "pixel"], //propiedrad con array de objetos para filtrar 
      colores: ["red", "green", "yellow", "blue", "black", "gray"], //colores para usar como fuente, array de objetos 
      filtro_seleccionado: "Selecciona", //string llamado para que aparezca "Selecciona en el select"
      color_seleccionado: "Selecciona", // string llamado para que aparezca en el select de color a seleccionar
      size: null, //null para que tome valor seleccionado de usuario, numero
      image_fuente: "", //propiedad con valor string vacio para que ingrese imagen obtenida
    };
  },
  methods: {
      //metodo mostrar gato 
    mostrar_gato() {
            //concanetacion de propiedades asignadas, seran dinamicas segun el usuario asigne
      this.image_fuente = `https://cataas.com/cat/gif/says/${this.title}?filter=${this.filtro_seleccionado}&color=${this.color_seleccionado}&size=${this.size}`;
    },
  },
};
</script>

<style>

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
 
}

.informacion {
  max-width: 800px;
  margin: auto;
 
}
/* enunciado */ 
.titulo {
  text-align: center;
  padding: 40px;
  background-color: #0c0458;
  color: #8ea6b9;
  font-weight: bolder;
  font-size: 30px;
}


.Filtros {
  padding : 10px;
  margin: 20px;
  background-color: #9603404f;
}

.datos {
  margin: 10px 0;
  text-align: center;
  padding-left: 45px;
  color: #394854;
  font-size: 25px;
  font-weight: bold;
}
/* circulo informacion */ 
.color {
  display: inline-block;
  align-items: center;
  margin: 20px;
}

.circulo_color {
  width: 30px;
  height: 30px;
  border-radius: 50%;
  margin-left: 40px;
  display: inline-block;
}

.gif {
  padding: 20px 0 50px 0;
  background-color: #421550;
  text-align: center;
}


/* BOTON GENERADOR*/

.mostrar_gato_boton {
 
  margin: 20px;
  font-size: 20px;
  border-radius: 20px;
  border-color: rgba(1, 1, 204, 0.418);
  cursor: pointer;
}

</style>
