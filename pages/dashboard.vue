<template>
  <v-row justify="center" align="center">
    <v-col cols="12">
      <v-row justify="start" align="center">
        <v-col cols="6" class="pl-3 pr-2 py-3">
          <v-card height="44.5vh">
            <v-card-title class="headline">
              Total Launches
            </v-card-title>
            <v-card-text>
              <div id="chart1">
                <apexchart type="line" :height="chartHeight" :options="launchesChartOptions" :series="launchesSeries" ref="launchChart"></apexchart>
              </div>
            </v-card-text>
          </v-card>
        </v-col>
        <v-col cols="3" class="px-1 py-3">
          <v-card height="44.5vh">
            <v-card-title class="headline">
              Launch Success Rate
            </v-card-title>
            <div id="chart2"> 
              <apexchart type="donut" :height="chartHeight2" :options="srChartOptions" :series="srSeries" ref="srChart"></apexchart>
            </div>
          </v-card>
        </v-col>
        <v-col cols="3" class="pl-2 pr-3 py-3">
          <v-card height="44.5vh">
            <v-card-title class="headline">
              Launch Locations
            </v-card-title>
            <div id="chart3">
              <apexchart type="donut" :height="chartHeight2" :options="launchpadChartOptions" :series="launchpadSeries" ref="launchpadChart"></apexchart>
            </div>
          </v-card>
        </v-col>
      </v-row>
      <v-row justify="start" align="center">
        <v-col cols="6" class="pl-3 pr-2 py-3">
          <v-card height="44.5vh">
            <v-card-title class="headline">
              Total Payload Sent to Space (kg)
            </v-card-title>
            <v-card-text>
              <div id="chart4">
                <apexchart type="line" :height="chartHeight" :options="payloadChartOptions" :series="payloadSeries" ref="payloadChart"></apexchart>
              </div>
            </v-card-text>
          </v-card>
        </v-col>
        <v-col cols="3" class="px-1 py-3">
          <v-card height="44.5vh">
            <v-card-title class="headline">
              Rocket Type Success Rate
            </v-card-title>
            <v-card-text>
              <div id="chart5">
                <apexchart type="bar" :height="chartHeight" :options="rocketChartOptions" :series="rocketSeries" ref="rocketChart"></apexchart>
              </div>
            </v-card-text>
          </v-card>
        </v-col>
        <v-col cols="3" class="pl-2 pr-3 py-3">
          <v-card height="44.5vh">
            <v-card-title class="headline">
              Landing Locations
            </v-card-title>
            <div id="chart6">
              <apexchart type="donut" :height="chartHeight2" :options="landpadChartOptions" :series="landpadSeries" ref="landpadChart"></apexchart>
            </div>
          </v-card>
        </v-col>
      </v-row>
    </v-col>
  </v-row>
</template>

<script>
const axios = require('axios');
import VueApexCharts from 'vue-apexcharts'
export default {
  components: {
    apexchart: VueApexCharts,
  },
  head() {
    return {
      title: "Dashboard"
    };
  },
  data () {
    return {
      launchesSeries: [{
        name: "Launches",
        data: []
      }],
      srSeries: [],
      launchpadSeries: [],
      landpadSeries: [],
      rocketSeries: [{
        name: 'Rockets',
        data: [30, 40, 35, 50, 49, 60, 70, 91]
      }],
      payloadSeries: [{
        name: "Payloads",
        data: []
      }],
      launchesChartOptions: {
        chart: {
          id: 'launchChart',
          type: 'line',
          toolbar: {
            show: true,
            offsetX: 0,
            offsetY: 0,
            tools: {
              download: false,
              selection: true,
              zoom: true,
              zoomin: false,
              zoomout: false,
              pan: true,
              reset: true | '<v-icon size="12px">mdi-restore</v-icon>',
              customIcons: []
            },
          },
        },
        annotations: {
          xaxis: [
            {
              x: new Date().getTime(),
              strokeDashArray: 0,
              borderColor: '#00E396',
              label: {
                borderColor: '#00E396',
                orientation: 'horizontal',
                text: 'Current Date'
              }
            }
          ]
        },
        stroke: {
          curve: 'straight'
        },
        grid: {
          borderColor: '#FFFFFF',
          xaxis: {
            lines: {
              show: true,
            }
          },
          yaxis: {
            lines: {
              show: true,
            },
          },
        },
        xaxis: {
          type: "datetime",
          labels: {
            style: {
              colors: '#FFFFFF',
            }
          },
          axisBorder:{
            show: true
          }
        },
        yaxis: {
          labels: {
            style: {
              colors: '#FFFFFF',
            }
          },
          axisBorder:{
            show: true
          }
        }
      },
      srChartOptions: {
        labels: ['Success', 'Fail', 'TBD'],
        colors: ['#008ffb', '#ff4560', '#ffffff'],
        plotOptions: {
          pie: {
            donut: {
              labels: {
                show: true,
              }
            }
          }
        },
        legend: {
          show: true,
          position: 'right',
          labels: {
            colors: '#FFFFFF',
            useSeriesColors: false
          }
        },
      },
      launchpadChartOptions: {
        labels: [],
        plotOptions: {
          pie: {
            donut: {
              labels: {
                show: true,
              }
            }
          }
        },
        legend: {
          show: true,
          position: 'right',
          labels: {
            colors: '#FFFFFF',
            useSeriesColors: false
          }
        },
      },
      landpadChartOptions: {
        labels: [],
        plotOptions: {
          pie: {
            donut: {
              labels: {
                show: true,
              }
            }
          }
        },
        legend: {
          show: true,
          position: 'right',
          labels: {
            colors: '#FFFFFF',
            useSeriesColors: false
          }
        },
      },
      rocketChartOptions: {
        chart: {
          id: 'rocketChart',
          height: 350,
          type: 'bar',
          toolbar: {
            show: false,
          },
        },
        xaxis: {
          categories: [],
          labels: {
            style: {
              colors: '#FFFFFF',
            }
          },
          axisBorder:{
            show: true
          }
        },
        yaxis: {
          labels: {
            style: {
              colors: '#FFFFFF',
            }
          },
          axisBorder:{
            show: true
          }
        }
      },
      payloadChartOptions: {
        chart: {
          id: 'payloadChart',
          type: 'line',
          toolbar: {
            show: true,
            offsetX: 0,
            offsetY: 0,
            tools: {
              download: false,
              selection: true,
              zoom: true,
              zoomin: false,
              zoomout: false,
              pan: true,
              reset: true | '<v-icon size="12px">mdi-restore</v-icon>',
              customIcons: []
            },
          },
        },
        annotations: {
          xaxis: [
            {
              x: new Date().getTime(),
              strokeDashArray: 0,
              borderColor: '#00E396',
              label: {
                borderColor: '#00E396',
                orientation: 'horizontal',
                text: 'Current Date'
              }
            }
          ]
        },
        stroke: {
          curve: 'straight'
        },
        grid: {
          borderColor: '#FFFFFF',
          xaxis: {
            lines: {
              show: true,
            }
          },
          yaxis: {
            lines: {
              show: true,
            },
          },
        },
        xaxis: {
          type: "datetime",
          labels: {
            style: {
              colors: '#FFFFFF',
            }
          },
          axisBorder:{
            show: true
          }
        },
        yaxis: {
          labels: {
            style: {
              colors: '#FFFFFF',
            },
            formatter: function(val, index) {
              return val.toFixed(0);
            }
          },
          axisBorder:{
            show: true
          }
        }
      },
      launches: [],
      payloads: [],
      rockets:[],
      launchpads: [],
      landpads: [],
      chartHeight: 325,
    }
  },
  created() {
    this.chartHeight = ((Math.max(document.documentElement.clientHeight || 0, window.innerHeight || 0) - 64)/2)-111
    this.chartHeight2 = ((Math.max(document.documentElement.clientHeight || 0, window.innerHeight || 0) - 64)/2)-81
    console.log(this.chartHeight)
    window.addEventListener("resize", this.resizeHandler);
  },
  destroyed() {
    window.removeEventListener("resize", this.resizeHandler);
  },
  mounted(){
    this.init();
  },
  methods:{
    resizeHandler(){
      this.chartHeight = ((Math.max(document.documentElement.clientHeight || 0, window.innerHeight || 0) - 64)/2)-111
      this.chartHeight2 = ((Math.max(document.documentElement.clientHeight || 0, window.innerHeight || 0) - 64)/2)-81
    },
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
        that.prepareSuccessRateSeries()
        axios.get('https://api.spacexdata.com/v4/payloads')
        .then(function (response) {
          response.data.forEach(function(element) {
            that.payloads.push(element)
          })
          that.prepareTotalPayloadSeries()
          axios.get('https://api.spacexdata.com/v4/rockets')
          .then(function (response) {
            response.data.forEach(function(element) {
              that.rockets.push(element)
            })
            that.prepareRocketSeries()
            axios.get('https://api.spacexdata.com/v4/launchpads')
            .then(function (response) {
              response.data.forEach(function(element) {
                that.launchpads.push(element)
              })
              that.prepareLaunchpadSeries()
              axios.get('https://api.spacexdata.com/v4/landpads')
              .then(function (response) {
                response.data.forEach(function(element) {
                  that.landpads.push(element)
                })
                that.prepareLandpadSeries()
              })
              .catch(function (error) {
                console.log(error);
              })
            })
            .catch(function (error) {
              console.log(error);
            })
          })
          .catch(function (error) {
            console.log(error);
          })
        })
        .catch(function (error) {
          console.log(error);
        })
      })
      .catch(function (error) {
        console.log(error);
      })
    },
    prepareTotalLaunchSeries(){
      var that = this
      var total_launches = 0
      var newSeriesData = []

      this.launches.sort(function(a, b) {
        var keyA = new Date(a.date_utc), keyB = new Date(b.date_utc);
        if (keyA < keyB) return -1;
        if (keyA > keyB) return 1;
        return 0;
      });
      
      this.launches.forEach(function(element) {
        total_launches = total_launches + 1
        var object = {
          x: element.date_utc,
          y: total_launches
        }
        newSeriesData.push(object)
      })

      this.launchesSeries = [{
        name: "Launches",
        data: newSeriesData
      }]
    },
    prepareSuccessRateSeries(){
      var that = this
      this.launches.sort(function(a, b) {
        var keyA = new Date(a.date_utc), keyB = new Date(b.date_utc);
        if (keyA < keyB) return -1;
        if (keyA > keyB) return 1;
        return 0;
      });

      var successCount = 0
      var failCount = 0
      var tbdCount = 0
      this.launches.forEach(function(element) {
        if(element.success == true) {
          successCount = successCount + 1
        } else if(element.success == false) {
          failCount = failCount + 1
        } else if(element.success == null) {
          tbdCount = tbdCount + 1
        }
      })

      this.srSeries = [successCount, failCount, tbdCount]
    },
    prepareTotalPayloadSeries(){
      var that = this
      var seriesTemp = []
      var total_payload_kg = 0
      this.payloads.forEach(function(element) {
        var relatedLaunch = that.launches.find(x => x.id === element.launch)
        if(typeof relatedLaunch !== "undefined") {
          element.launchDate = relatedLaunch.date_utc
        }
      })

      this.payloads.sort(function(a, b) {
        var keyA = new Date(a.launchDate), keyB = new Date(b.launchDate);
        if (keyA < keyB) return -1;
        if (keyA > keyB) return 1;
        return 0;
      });

      var prevDate = ""
      var currDate = ""
      
      this.payloads.forEach(function(element) {
        if(typeof element.launchDate !== "undefined") {
          currDate = element.launchDate
          if(prevDate === currDate) {
            prevDate = currDate
            total_payload_kg = total_payload_kg + element.mass_kg
          } else {
            if(prevDate !== ""){
              var object = {
                x: prevDate,
                y: total_payload_kg,
              }
              seriesTemp.push(object)
            }
            total_payload_kg = total_payload_kg + element.mass_kg
            prevDate = currDate
          }
        }
      })
      
      this.payloadSeries = [{
        name: "Payloads",
        data: seriesTemp
      }]
    },
    prepareRocketSeries(){
      var seriesTemp = []
      var categoriesTemp = []
      this.rockets.forEach(function(element) {
        categoriesTemp.push(element.name)
        seriesTemp.push(element.success_rate_pct)
      })

      this.rocketSeries = [{
        name: "Rockets",
        data: seriesTemp
      }]

      this.rocketChartOptions = {
        chart: {
          id: 'rocketChart'
        },
        xaxis: {
          categories: categoriesTemp,
          labels: {
            style: {
              colors: '#FFFFFF',
            }
          },
          axisBorder:{
            show: true
          }
        },
        yaxis: {
          labels: {
            style: {
              colors: '#FFFFFF',
            }
          },
          axisBorder:{
            show: true
          }
        }
      }
    },
    prepareLaunchpadSeries() {
      var seriesTemp = []
      var categoriesTemp = []

      this.launchpads.sort(function(a, b) {
        var keyA = new Date(a.launch_attempts), keyB = new Date(b.launch_attempts);
        if (keyA < keyB) return -1;
        if (keyA > keyB) return 1;
        return 0;
      });

      this.launchpads.forEach(function(element) {
        categoriesTemp.push(element.name)
        seriesTemp.push(element.launch_attempts)
      })

      this.launchpadSeries = seriesTemp

      this.launchpadChartOptions = {
        labels: categoriesTemp,
        plotOptions: {
          pie: {
            donut: {
              labels: {
                show: true,
              }
            }
          }
        },
        legend: {
          show: true,
          labels: {
            colors: '#FFFFFF',
            useSeriesColors: false
          }
        }
      }
    },
    prepareLandpadSeries() {
      var seriesTemp = []
      var categoriesTemp = []

      this.landpads.sort(function(a, b) {
        var keyA = new Date(a.landing_attempts), keyB = new Date(b.landing_attempts);
        if (keyA < keyB) return -1;
        if (keyA > keyB) return 1;
        return 0;
      });

      this.landpads.forEach(function(element) {
        categoriesTemp.push(element.name)
        seriesTemp.push(element.landing_attempts)
      })

      this.landpadSeries = seriesTemp

      this.landpadChartOptions = {
        labels: categoriesTemp,
        plotOptions: {
          pie: {
            donut: {
              labels: {
                show: true,
              }
            }
          }
        },
        legend: {
          show: true,
          labels: {
            colors: '#FFFFFF',
            useSeriesColors: false
          }
        }
      }
    }
  }
}
</script>
<style>
.apexcharts-tooltip {
  background: #ffffff;
  color: black;
}

.container, .layout {
  height: 100%;
}

.xs6 {
  display: flex;
  flex-direction: column;
}

.height {
  flex: 1 1 auto;
}
</style>
