<template> 
  <div> <!-- DIV UNICO -->
    <!-- a traves de moustache usamos el componente tarea -->
     <ul class="text">           
            <li> {{tarea}}</li>
        </ul>
    <!-- creo boton con la funcion borrar para realizar la eliminacion
    del contenido, viene desde emit  (Evento click)-->
    <button class="boton_borrar" @click="borrar_tarea">Eliminar</button>
  </div>
</template>

<script>
// Componente tarea
export default {
 
  name: "tarea",  // Nombre  componente
  props: {// propiedades pasadas por el componente padre como tipo string  y number
    tarea: String,
    indice: Number,
  },
  methods: { 
    borrar_tarea() {
      /*propiedades pasadas x componente padre a comp.hijo, traves de emit
       queriendo generar una llamada con valor eliminar, recibiendo esta info 
       el componente padre.*/
      this.$emit("eliminar_tareita", this.indice);
    },
  },
};
</script>

<style></style>
