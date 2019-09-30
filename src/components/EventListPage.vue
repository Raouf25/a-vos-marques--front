<template>
  <div class="container">
    <v-card :elevation="24"
            class="mx-auto pa-6">
      <div class="row">
        <div class="col-md-5">
          <div id="map" class="map"></div>
        </div>
        <div class="col-md-7">
          <v-container fluid>
            <v-row align="center">
              <v-col cols="6">
                <v-subheader>Ville</v-subheader>
              </v-col>
              <v-col cols="6">
                <v-select v-model="e1"
                          :items="states"
                          menu-props="auto"
                          label="Select"
                          hide-details
                          prepend-icon="map"
                          v-on:input="changeRoute(`${e1}`)"
                          single-line
                ></v-select>
              </v-col>
            </v-row>
          </v-container>
          <v-data-table :headers="headers"
                        :items="items"
                        :items-per-page="5"
                        class="elevation-1">
          </v-data-table>
        </div>
      </div>
    </v-card>
  </div>
</template>

<script>
    import L from 'leaflet';
  export default {
    data: () => {
      return {
        map: null,
        tileLayer: null,
        e1: 'Florida',
        layerGroup: null,
        markerLayer: null,
        region: [],
        states: [],

        items: [],
        headers: [
          {text: 'id', value: 'idEvent'},
          {text: 'Title event', value: 'titleEvent'},
          {text: 'Date event', value: 'dateEvent'},
        ],
      }
    },


    mounted() {
      this.initMap();
    },

    created () {
      this.getAllTowns();
    },

    methods: {
      getAllTowns(){
        console.log("look for town list from rest Api");
      },

      initMap() {
        // // Creating map options
        var mapOptions = {
          center: [46.603354, 1.8883335],
          zoom: 6
        };

        this.map = L.map('map', mapOptions);
        this.tileLayer = L.tileLayer('https://cartodb-basemaps-{s}.global.ssl.fastly.net/rastertiles/voyager/{z}/{x}/{y}.png');
        this.tileLayer.addTo(this.map);
      },

      changeRoute(a) {
        console.log(a);
        console.log("look for stadiums in city postal code a  from rest Api");
        this.getEvent(a);
      },

      getEvent(a) {
        console.log("look for events in city postal code a  from rest Api");
        console.log(a);
      },

    },
  }
</script>

<style>
  .map {
    height: 450px;
  }
</style>
