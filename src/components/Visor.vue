<template>
  <div v-if="ciudad" >
    <b-card no-body class="overflow-hidden" border-variant="secondary">
      <b-row no-gutters>
        <b-col md="7">
          <b-card-body :title="`${ciudad[0].nombre}`" :sub-title="this.ciudad[0].fecha | hora">
            <b-card-text>
              <span>{{ciudad[0].estado | capitalize}}</span>
              <img :src="`http://openweathermap.org/img/wn/${ ciudad[0].icon }.png`" alt="Estado" >
            </b-card-text>
          </b-card-body>
        </b-col>
          <b-col md="5">
            <h1 class="display-1 mt-3">{{ this.ciudad[0].temp | tempEntero }}º</h1>
        </b-col>
      </b-row>
    </b-card>
    <b-card no-body class="overflow-hidden" border-variant="secondary">
      <b-row no-gutters>
        <b-col md="7">
          <b-card-body :title="`${ciudad[1].nombre}`" :sub-title="this.ciudad[1].fecha | hora">
            <b-card-text>
              <span>{{ciudad[1].estado | capitalize}}</span>
              <img :src="`http://openweathermap.org/img/wn/${ ciudad[1].icon }.png`" alt="Estado" >
            </b-card-text>
          </b-card-body>
        </b-col>
          <b-col md="5">
            <h1 class="display-1 mt-3">{{ this.ciudad[1].temp | tempEntero }}º</h1>
        </b-col>
      </b-row>
    </b-card>
  </div>
  <div v-else>
     <p class="bg-danger text-white font-weight-bold rounded">No se encontró la ubicación</p>
  </div>
</template>

<script>
export default {
    data () {
      return {
        fecha: null
      }
    },
    props: {
        ciudad: Array
    },
    // Computed properties
    computed: {
      /*hora: function(){
        if(this.ciudad.fecha){
          let fecha = new Date(this.ciudad.fecha*1000);
          return fecha.getHours()+":"+fecha.getMinutes();
        }else{
          return "";
        }
      }*/
    },
    // Filtro para poner en mayusculas un string
    filters: {
      capitalize: function(value) {
         return value.toUpperCase();
      },
      tempEntero: function(value){
        return parseInt(value);
      },
      hora: function(value){
        let fecha = new Date(value*1000);
        return fecha.getHours()+":"+fecha.getMinutes();
      }
    }
}
</script>

<style>
</style>