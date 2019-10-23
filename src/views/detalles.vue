<template>
  <div id="details" class="text-center">
    <buscador @change="cargaDatos"></buscador>
    <div v-if="iniciado" >
      <visor :datosCiudad="datosActuales"></visor>
    </div>
  </div>
</template>

<script>
 export default{
    data () {
      return {
        datosActuales: null,
        iniciado: false
      }
    },
    methods: {
      cargaDatos (detallesBuscador) {
        this.iniciado = true
        this.datosActuales = detallesBuscador
      }
    }
}
</script>

<style lang="scss">
$tamaño-icono: 4em;
.icono{
  width: $tamaño-icono;
}

</style>
