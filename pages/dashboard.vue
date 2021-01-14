<template>
  <v-row justify="center" align="center">
    <v-col cols="12">
      <v-row justify="start" align="center">
        <v-col cols="6">
          <v-card>
            <v-card-title class="headline">
              Total Launches
            </v-card-title>
            <v-card-text>
              <div id="chart">
                <apexchart type="line" height="350" :options="chartOptions" :series="series" ref="launchChart"></apexchart>
              </div>
            </v-card-text>
          </v-card>
        </v-col>
        <v-col cols="6">
          <v-card>
            <v-card-title class="headline">
              Cores
            </v-card-title>
          </v-card>
        </v-col>
      </v-row>
    </v-col>
  </v-row>
</template>

<script>
const axios = require('axios');
import LaunchpadMap from '@/components/launchpad_map.vue'
import LandingpadMap from '@/components/landingpad_map.vue'
import VueApexCharts from 'vue-apexcharts'
export default {
  components: {
    LaunchpadMap,
    LandingpadMap,
    apexchart: VueApexCharts,
  },
  data () {
    return {
      series: [{
        name: "Launches",
        data: []
      }],
      chartOptions: {
        chart: {
          id: 'launchChart',
          height: 350,
          type: 'line',
          zoom: {
            enabled: false
          }
        },
        stroke: {
          curve: 'straight'
        },
        grid: {
          xaxis: {
            lines: {
              show: true,
            }
          },
          yaxis: {
            lines: {
              show: true,
            }
          },
        },
        xaxis: {
          type: 'category'
        }
      },
      launches: [],
    }
  },
  mounted(){
    this.init();
  },
  methods:{
    init(){
      var that = this
      axios.get('https://api.spacexdata.com/v4/launches')
      .then(function (response) {
        response.data.forEach(function(element) {
          var object = {
            success: element.success,
            failures: element.failures,
            crew: element.crew,
            launchpad: element.launchpad,
            name: element.name,
            date_utc: element.date_utc.split('T')[0],
            date_unix: element.date_unix,
            upcoming: element.upcoming,
            id: element.id,
          }
          that.launches.push(object)
        })
        that.prepareTotalLaunchSeries()
      })
      .catch(function (error) {
        console.log(error);
      })
    },
    prepareTotalLaunchSeries(){
      var that = this
      var res = []
      var counter = 0
      this.launches.forEach(function(element) {
        var year = parseInt(element.date_utc.split("-")[0])
        var month = parseInt(element.date_utc.split("-")[1], 10)
        if(!res[year]) res[year] = []
        res[year].push(element)
      })
      var total_launches = 0
      var newSeriesData = []
      res.forEach(function(element, year) {
        total_launches = total_launches+element.length
        var object = {
          x: year.toString(),
          y: total_launches
        }
        newSeriesData.push(object)
      })
      this.series = [{
        data: newSeriesData
      }]
    }
  },
}
</script>
