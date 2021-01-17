<template>
  <v-row justify="center" align="center">
    <v-col cols="12">
      <v-row justify="start" align="center">
        <v-col cols="6">
          <v-card>
            <v-card-title class="headline">
              Capsules
              <v-spacer></v-spacer>
              <v-text-field
                v-model="capsuleSearch"
                append-icon="mdi-magnify"
                label="Search"
                single-line
                hide-details
              ></v-text-field>
            </v-card-title>
            <v-data-table
              :headers="capsuleHeaders"
              :items="capsules"
              :search="capsuleSearch"
              :items-per-page="5"
              :single-expand="true"
              :header-props="{ sortIcon: null }"
              show-expand
              dense
              fixed-header
              height="21vh"
              class="elevation-1"
            >
              <template v-slot:item.id="{item}">
                <NuxtLink :to="{name: 'details', params: { id: item.id, type: 'capsule' } }">{{ item.id }}</NuxtLink>
              </template>
              <template v-slot:expanded-item="{ headers, item }">
                <td :colspan="headers.length">
                  Last update: {{ item.last_update }}
                </td>
              </template>
            </v-data-table>
          </v-card>
        </v-col>
        <v-col cols="6">
          <v-card>
            <v-card-title class="headline">
              Cores
              <v-spacer></v-spacer>
              <v-text-field
                v-model="coreSearch"
                append-icon="mdi-magnify"
                label="Search"
                single-line
                hide-details
              ></v-text-field>
            </v-card-title>
            <v-data-table
              :headers="coreHeaders"
              :items="cores"
              :search="coreSearch"
              :items-per-page="5"
              :single-expand="true"
              :header-props="{ sortIcon: null }"
              show-expand
              dense
              fixed-header
              height="21vh"
              class="elevation-1"
            >
              <template v-slot:item.id="{item}">
                <NuxtLink :to="{name: 'details', params: { id: item.id, type: 'core' } }">{{ item.id }}</NuxtLink>
              </template>
              <template v-slot:expanded-item="{ headers, item }">
                <td :colspan="headers.length">
                  Last update: {{ item.last_update }}
                </td>
              </template>
            </v-data-table>
          </v-card>
        </v-col>
      </v-row>
      <v-row justify="start" align="center">
        <v-col cols="6">
          <v-card>
            <v-card-title class="headline">
              Crew
              <v-spacer></v-spacer>
              <v-text-field
                v-model="crewSearch"
                append-icon="mdi-magnify"
                label="Search"
                single-line
                hide-details
              ></v-text-field>
            </v-card-title>
            <v-data-table
              :headers="crewHeaders"
              :items="crews"
              :search="crewSearch"
              :items-per-page="5"
              :header-props="{ sortIcon: null }"
              dense
              fixed-header
              height="21vh"
              class="elevation-1"
            >
              <template v-slot:item.id="{item}">
                <NuxtLink :to="{name: 'details', params: { id: item.id, type: 'crew' } }">{{ item.id }}</NuxtLink>
              </template>
              <template v-slot:item.image="{item}">
                <a target="_blank" :href="item.image">
                  <v-icon size="12px">{{ 'mdi-image' }}</v-icon>
                </a>
              </template>
              <template v-slot:item.wiki="{ item }">
                <a target="_blank" :href="item.wiki">
                  <v-icon size="12px">{{ 'mdi-wikipedia' }}</v-icon>
                </a>
              </template>
            </v-data-table>
          </v-card>
        </v-col>
        <v-col cols="6">
          <v-card>
            <v-card-title class="headline">
              Dragons
              <v-spacer></v-spacer>
              <v-text-field
                v-model="dragonSearch"
                append-icon="mdi-magnify"
                label="Search"
                single-line
                hide-details
              ></v-text-field>
            </v-card-title>
            <v-data-table
              :headers="dragonHeaders"
              :items="dragons"
              :search="dragonSearch"
              :items-per-page="5"
              :single-expand="true"
              :header-props="{ sortIcon: null }"
              show-expand
              dense
              fixed-header
              height="21vh"
              class="elevation-1"
            >
              <template v-slot:item.id="{item}">
                <NuxtLink :to="{name: 'details', params: { id: item.id, type: 'dragon' } }">{{ item.id }}</NuxtLink>
              </template>
              <template v-slot:item.flickr_images="{item}">
                <a target="_blank" :href="item.flickr_images">
                  <v-icon size="12px">{{ 'mdi-image' }}</v-icon>
                </a>
              </template>
              <template v-slot:item.wikipedia="{ item }">
                <a target="_blank" :href="item.wikipedia">
                  <v-icon size="12px">{{ 'mdi-wikipedia' }}</v-icon>
                </a>
              </template>
              <template v-slot:expanded-item="{ headers, item }">
                <td :colspan="headers.length">
                  Description: {{ item.description }}
                </td>
              </template>
            </v-data-table>
          </v-card>
        </v-col>
      </v-row>
      <v-row justify="start" align="center">
        <v-col cols="6">
          <v-card>
            <v-card-title class="headline">
              Launches
              <v-spacer></v-spacer>
              <v-text-field
                v-model="launchSearch"
                append-icon="mdi-magnify"
                label="Search"
                single-line
                hide-details
              ></v-text-field>
            </v-card-title>
            <v-data-table
              :headers="launchHeaders"
              :items="launches"
              :search="launchSearch"
              :items-per-page="5"
              :single-expand="true"
              :header-props="{ sortIcon: null }"
              show-expand
              dense
              fixed-header
              height="21vh"
              class="elevation-1"
            >
              <template v-slot:item.id="{item}">
                <NuxtLink :to="{name: 'details', params: { id: item.id, type: 'launch' } }">{{ item.id }}</NuxtLink>
              </template>
              <template v-slot:expanded-item="{ headers, item }">
                <td :colspan="headers.length">
                  Description: {{ item.details }}
                </td>
              </template>
            </v-data-table>
          </v-card>
        </v-col>
        <v-col cols="6">
          <v-card>
            <v-card-title class="headline">
              Launchpads
              <v-spacer></v-spacer>
              <v-text-field
                v-model="launchpadSearch"
                append-icon="mdi-magnify"
                label="Search"
                single-line
                hide-details
              ></v-text-field>
            </v-card-title>
            <v-data-table
              :headers="launchpadHeaders"
              :items="launchpads"
              :search="launchpadSearch"
              :items-per-page="5"
              :header-props="{ sortIcon: null }"
              dense
              fixed-header
              height="21vh"
              class="elevation-1"
            >
              <template v-slot:item.id="{item}">
                <NuxtLink :to="{name: 'details', params: { id: item.id, type: 'launchpad' } }">{{ item.id }}</NuxtLink>
              </template>
            </v-data-table>
          </v-card>
        </v-col>
      </v-row>
      <v-row justify="start" align="center">
        <v-col cols="6">
          <v-card>
            <v-card-title class="headline">
              Landpads
              <v-spacer></v-spacer>
              <v-text-field
                v-model="landpadSearch"
                append-icon="mdi-magnify"
                label="Search"
                single-line
                hide-details
              ></v-text-field>
            </v-card-title>
            <v-data-table
              :headers="landpadHeaders"
              :items="landpads"
              :search="landpadSearch"
              :items-per-page="5"
              :single-expand="true"
              :header-props="{ sortIcon: null }"
              show-expand
              dense
              fixed-header
              height="21vh"
              class="elevation-1"
            >
              <template v-slot:item.id="{item}">
                <NuxtLink :to="{name: 'details', params: { id: item.id, type: 'landpad' } }">{{ item.id }}</NuxtLink>
              </template>
              <template v-slot:item.wikipedia="{ item }">
                <a target="_blank" :href="item.wikipedia">
                  <v-icon size="12px">{{ 'mdi-wikipedia' }}</v-icon>
                </a>
              </template>
              <template v-slot:expanded-item="{ headers, item }">
                <td :colspan="headers.length">
                  Description: {{ item.details }}
                </td>
              </template>
            </v-data-table>
          </v-card>
        </v-col>
        <v-col cols="6">
          <v-card>
            <v-card-title class="headline">
              Payloads
              <v-spacer></v-spacer>
              <v-text-field
                v-model="payloadSearch"
                append-icon="mdi-magnify"
                label="Search"
                single-line
                hide-details
              ></v-text-field>
            </v-card-title>
            <v-data-table
              :headers="payloadHeaders"
              :items="payloads"
              :search="payloadSearch"
              :items-per-page="5"
              :header-props="{ sortIcon: null }"
              dense
              fixed-header
              height="21vh"
              class="elevation-1"
            >
              <template v-slot:item.id="{item}">
                <NuxtLink :to="{name: 'details', params: { id: item.id, type: 'payload' } }">{{ item.id }}</NuxtLink>
              </template>
            </v-data-table>
          </v-card>
        </v-col>
      </v-row>
      <v-row justify="start" align="center">
        <v-col cols="6">
          <v-card>
            <v-card-title class="headline">
              Fairings
              <v-spacer></v-spacer>
              <v-text-field
                v-model="fairingSearch"
                append-icon="mdi-magnify"
                label="Search"
                single-line
                hide-details
              ></v-text-field>
            </v-card-title>
            <v-data-table
              :headers="fairingHeaders"
              :items="fairings"
              :search="fairingSearch"
              :items-per-page="5"
              :header-props="{ sortIcon: null }"
              dense
              fixed-header
              height="21vh"
              class="elevation-1"
            >
              <template v-slot:item.serial="{item}">
                <NuxtLink :to="{name: 'details', params: { id: item.serial, type: 'fairing' } }">{{ item.serial }}</NuxtLink>
              </template>
            </v-data-table>
          </v-card>
        </v-col>
        <v-col cols="6">
          <v-card>
            <v-card-title class="headline">
              Rockets
              <v-spacer></v-spacer>
              <v-text-field
                v-model="rocketSearch"
                append-icon="mdi-magnify"
                label="Search"
                single-line
                hide-details
              ></v-text-field>
            </v-card-title>
            <v-data-table
              :headers="rocketHeaders"
              :items="rockets"
              :search="rocketSearch"
              :items-per-page="5"
              :single-expand="true"
              :header-props="{ sortIcon: null }"
              show-expand
              dense
              fixed-header
              height="21vh"
              class="elevation-1"
            >
              <template v-slot:item.id="{item}">
                <NuxtLink :to="{name: 'details', params: { id: item.id, type: 'rocket' } }">{{ item.id }}</NuxtLink>
              </template>
              <template v-slot:item.wikipedia="{ item }">
                <a target="_blank" :href="item.wikipedia">
                  <v-icon size="12px">{{ 'mdi-wikipedia' }}</v-icon>
                </a>
              </template>
              <template v-slot:expanded-item="{ headers, item }">
                <td :colspan="headers.length">
                  Description: {{ item.description }}
                </td>
              </template>
            </v-data-table>
          </v-card>
        </v-col>
      </v-row>
      <v-row justify="start" align="center">
        <v-col cols="6">
          <v-card>
            <v-card-title class="headline">
              Ships
              <v-spacer></v-spacer>
              <v-text-field
                v-model="shipSearch"
                append-icon="mdi-magnify"
                label="Search"
                single-line
                hide-details
              ></v-text-field>
            </v-card-title>
            <v-data-table
              :headers="shipHeaders"
              :items="ships"
              :search="shipSearch"
              :items-per-page="5"
              :header-props="{ sortIcon: null }"
              dense
              fixed-header
              height="21vh"
              class="elevation-1"
            >
              <template v-slot:item.id="{item}">
                <NuxtLink :to="{name: 'details', params: { id: item.id, type: 'ship' } }">{{ item.id }}</NuxtLink>
              </template>
              <template v-slot:item.image="{ item }">
                <a target="_blank" :href="item.image">
                  <v-icon size="12px">{{ 'mdi-image' }}</v-icon>
                </a>
              </template>
              <template v-slot:item.link="{ item }">
                <a target="_blank" :href="item.link">
                  <v-icon size="12px">{{ 'mdi-web' }}</v-icon>
                </a>
              </template>
            </v-data-table>
          </v-card>
        </v-col>
        <v-col cols="6">
          <v-card>
            <v-card-title class="headline">
              Starlinks
              <v-spacer></v-spacer>
              <v-text-field
                v-model="starlinkSearch"
                append-icon="mdi-magnify"
                label="Search"
                single-line
                hide-details
              ></v-text-field>
            </v-card-title>
            <v-data-table
              :headers="starlinkHeaders"
              :items="starlinks"
              :search="starlinkSearch"
              :items-per-page="5"
              :header-props="{ sortIcon: null }"
              dense
              fixed-header
              height="21vh"
              class="elevation-1"
            >
              <template v-slot:item.id="{item}">
                <NuxtLink :to="{name: 'details', params: { id: item.id, type: 'starlink' } }">{{ item.id }}</NuxtLink>
              </template>
              <template v-slot:item.launch="{item}">
                <NuxtLink :to="{name: 'details', params: { id: item.launch, type: 'launch' } }">{{ item.launch }}</NuxtLink>
              </template>
            </v-data-table>
          </v-card>
        </v-col>
      </v-row>
    </v-col>
  </v-row>
</template>

<script>
const axios = require('axios');
export default {
  components: {
    
  },
  head() {
    return {
      title: "Data Overview"
    };
  },
  data () {
    return {
      capsuleSearch: '',
      coreSearch: '',
      crewSearch: '',
      dragonSearch: '',
      landpadSearch: '',
      launchSearch: '',
      launchpadSearch: '',
      payloadSearch: '',
      fairingSearch: '',
      rocketSearch: '',
      shipSearch: '',
      starlinkSearch: '',
      capsuleHeaders: [
        {text: 'ID', align: 'start', sortable: true, value: 'id', width: "20%"},
        {text: 'Serial', align: 'start', sortable: true, value: 'serial', width: "12%"},
        {text: 'Type', align: 'start', sortable: true, value: 'type', width: "15%"},
        {text: 'Status', align: 'start', sortable: true, value: 'status', width: "12%"},
        {text: 'Reuse', align: 'start', sortable: true, value: 'reuse', width: "15%"},
        {text: 'Land/Water Landings', align: 'start', sortable: true, value: 'landWater_landings', width: "28%"}
      ],
      coreHeaders:[
        {text: 'ID', align: 'start', sortable: true, value: 'id', width: "20%"},
        {text: 'Serial', align: 'start', sortable: true, value: 'serial', width: "10%"},
        {text: 'Block', align: 'start', sortable: true, value: 'block', width: "10%"},
        {text: 'Status', align: 'start', sortable: true, value: 'status', width: "10%"},
        {text: 'Reuse', align: 'start', sortable: true, value: 'reuse', width: "10%"},
        {text: 'RTLS Success Rate', align: 'start', sortable: true, value: 'rtls_landings_attempts', width: "20%"},
        {text: 'ASDS Success Rate', align: 'start', sortable: true, value: 'asds_landings_attempts', width: "20%"}
      ],
      crewHeaders:[
        {text: 'ID', align: 'start', sortable: true, value: 'id', width: "25%"},
        {text: 'Name', align: 'start', sortable: true, value: 'name', width: "25%"},
        {text: 'Agency', align: 'start', sortable: true, value: 'agency', width: "15%"},
        {text: 'No. Launches', align: 'start', sortable: true, value: 'launches.length', width: "15%"},
        {text: 'Image', align: 'start', sortable: true, value: 'image', width: "10%"},
        {text: 'Wikipedia', align: 'start', sortable: true, value: 'wiki', width: "10%"}
      ],
      dragonHeaders:[
        {text: 'ID', align: 'start', sortable: true, value: 'id', width: "20%"},
        {text: 'Name', align: 'start', sortable: true, value: 'name', width: "15%"},
        {text: 'Type', align: 'start', sortable: true, value: 'type', width: "10%"},
        {text: 'First Flight', align: 'start', sortable: true, value: 'first_flight', width: "20%"},
        {text: 'Payload (kg)', align: 'start', sortable: true, value: 'launch_payload_mass.kg', width: "10%"},
        {text: 'Orbit (years)', align: 'start', sortable: true, value: 'orbit_duration_yr', width: "10%"},
        {text: 'Image', align: 'start', sortable: true, value: 'flickr_images', width: "7%"},
        {text: 'Wikipedia', align: 'start', sortable: true, value: 'wikipedia', width: "7%"}
      ],
      landpadHeaders:[
        {text: 'ID', align: 'start', sortable: true, value: 'id', width: "20%"},
        {text: 'Name', align: 'start', sortable: true, value: 'full_name', width: "20%"},
        {text: 'Type', align: 'start', sortable: true, value: 'type', width: "10%"},
        {text: 'Status', align: 'start', sortable: true, value: 'status', width: "10%"},
        {text: 'Location', align: 'start', sortable: true, value: 'location', width: "30%"},
        {text: 'Success Rate', align: 'start', sortable: true, value: 'landing_attempt_success', width: "10%"},
        {text: 'Wikipedia', align: 'start', sortable: true, value: 'wikipedia', width: "5%"}
      ],
      launchHeaders:[
        {text: 'ID', align: 'start', sortable: true, value: 'id', width: "20%"},
        {text: 'Name', align: 'start', sortable: true, value: 'name', width: "15%"},
        {text: 'Flight No.', align: 'start', sortable: true, value: 'flight_number', width: "10%"},
        {text: 'Date (UTC)', align: 'start', sortable: true, value: 'date_utc', width: "34%"},
        {text: 'Success', align: 'start', sortable: true, value: 'success', width: "7%"},
        {text: 'Crew', align: 'start', sortable: true, value: 'crew.length', width: "7%"},
        {text: 'Upcoming', align: 'start', sortable: true, value: 'upcoming', width: "7%"},
      ],
      launchpadHeaders:[
        {text: 'ID', align: 'start', sortable: true, value: 'id', width: "20%"},
        {text: 'Name', align: 'start', sortable: true, value: 'full_name', width: "40%"},
        {text: 'Region', align: 'start', sortable: true, value: 'region', width: "10%"},
        {text: 'No. Rockets', align: 'start', sortable: true, value: 'rockets.length', width: "10%"},
        {text: 'Success Rate', align: 'start', sortable: true, value: 'launch_success_attempt', width: "10%"},
        {text: 'Status', align: 'start', sortable: true, value: 'status', width: "10%"},
      ],
      payloadHeaders:[
        {text: 'ID', align: 'start', sortable: true, value: 'id', width: "15%"},
        {text: 'Name', align: 'start', sortable: true, value: 'name', width: "20%"},
        {text: 'Customer', align: 'start', sortable: true, value: 'customers_string', width: "30%"},
        {text: 'Nationality', align: 'start', sortable: true, value: 'nationalities_string', width: "20%"},
        {text: 'Mass (kg)', align: 'start', sortable: true, value: 'mass_kg', width: "5%"},
        {text: 'Orbit', align: 'start', sortable: true, value: 'orbit', width: "5%"},
        {text: 'Reused', align: 'start', sortable: true, value: 'reused', width: "5%"}
      ],
      fairingHeaders:[
        {text: 'Serial', align: 'start', sortable: true, value: 'serial', width: "25%"},
        {text: 'Version', align: 'start', sortable: true, value: 'version', width: "10%"},
        {text: 'Status', align: 'start', sortable: true, value: 'status', width: "15%"},
        {text: 'Reuse Count', align: 'start', sortable: true, value: 'reuse', width: "10%"},
        {text: 'Net Landings', align: 'start', sortable: true, value: 'net_landing_success_attempts', width: "10%"},
        {text: 'Water Landings', align: 'start', sortable: true, value: 'water_landing_success_attempts', width: "10%"},
        {text: 'Last Update', align: 'start', sortable: true, value: 'last_update', width: "20%"}
      ],
      rocketHeaders:[
        {text: 'ID', align: 'start', sortable: true, value: 'id', width: "20%"},
        {text: 'Name', align: 'start', sortable: true, value: 'name', width: "25%"},
        {text: 'Type', align: 'start', sortable: true, value: 'type', width: "10%"},
        {text: 'Stages', align: 'start', sortable: true, value: 'stages', width: "10%"},
        {text: 'Engines', align: 'start', sortable: true, value: 'engines.number', width: "10%"},
        {text: 'Boosters', align: 'start', sortable: true, value: 'boosters', width: "10%"},
        {text: 'Success Rate (%)', align: 'start', sortable: true, value: 'success_rate_pct', width: "10%"},
        {text: 'Wikipedia', align: 'start', sortable: true, value: 'wikipedia', width: "10%"}
      ],
      shipHeaders:[
        {text: 'ID', align: 'start', sortable: true, value: 'id', width: "15%"},
        {text: 'Name', align: 'start', sortable: true, value: 'name', width: "25%"},
        {text: 'Type', align: 'start', sortable: true, value: 'type', width: "20%"},
        {text: 'Home Port', align: 'start', sortable: true, value: 'home_port', width: "25%"},
        {text: 'Active', align: 'start', sortable: true, value: 'active', width: "5%"},
        {text: 'Image', align: 'start', sortable: true, value: 'image', width: "5%"},
        {text: 'Link', align: 'start', sortable: true, value: 'link', width: "5%"}
      ],
      starlinkHeaders:[
        {text: 'ID', align: 'start', sortable: true, value: 'id', width: "20%"},
        {text: 'Version', align: 'start', sortable: true, value: 'version', width: "20%"},
        {text: 'Launch', align: 'start', sortable: true, value: 'launch', width: "20%"},
        {text: 'Height', align: 'start', sortable: true, value: 'height_km', width: "20%"},
        {text: 'Velocity', align: 'start', sortable: true, value: 'velocity_kms', width: "20%"}
      ],
      historyHeaders:[
        {text: 'ID', align: 'start', sortable: true, value: 'id'},
        {text: 'Serial', align: 'start', sortable: true, value: 'serial'},
        {text: 'Type', align: 'start', sortable: true, value: 'type'},
        {text: 'Status', align: 'start', sortable: true, value: 'status'},
        {text: 'Reuse Count', align: 'start', sortable: true, value: 'reuse'},
        {text: 'Land/Water Landings', align: 'start', sortable: true, value: 'landWater_landings'},
        {text: 'Last Update', align: 'start', sortable: true, value: 'last_update'}
      ],
      capsules: [],
      cores:[],
      crews:[],
      dragons:[],
      landpads:[],
      launches:[],
      launchpads:[],
      payloads:[],
      fairings:[],
      rockets:[],
      ships:[],
      starlinks:[],
    }
  },
  mounted(){
    this.init()
  },
  methods:{
    init(){
      var that = this
      axios.get('https://api.spacexdata.com/v4/capsules')
      .then(function (response) {
        response.data.forEach(function(element) {
          var object = {
            id: element.id,
            serial: element.serial,
            type: element.type,
            status: element.status,
            reuse: element.reuse_count,
            landWater_landings: element.land_landings+"/"+element.water_landings,
            last_update: element.last_update,
            launches: element.launches
          }
          that.capsules.push(object)
        })
      })
      .catch(function (error) {
        console.log(error);
      })
      axios.get('https://api.spacexdata.com/v4/cores')
      .then(function (response) {
        response.data.forEach(function(element) {
          var object = {
            block: element.block,
            reuse: element.reuse_count,
            rtls_attempts: element.rtls_attempts,
            rtls_landings: element.rtls_landings,
            rtls_landings_attempts: element.rtls_landings+'/'+element.rtls_attempts,
            asds_attempts: element.asds_attempts,
            asds_landings: element.asds_landings,
            asds_landings_attempts: element.asds_landings+'/'+element.asds_attempts,
            last_update: element.last_update,
            launches: element.launches,
            serial: element.serial,
            status: element.status,
            id: element.id,
          }
          that.cores.push(object)
        })
      })
      .catch(function (error) {
        console.log(error);
      })
      axios.get('https://api.spacexdata.com/v4/crew')
      .then(function (response) {
        response.data.forEach(function(element) {
          var object = {
            name: element.name,
            agency: element.agency,
            image: element.image,
            wiki: element.wikipedia,
            launches: element.launches,
            status: element.status,
            id: element.id,
          }
          that.crews.push(object)
        })
      })
      .catch(function (error) {
        console.log(error);
      })
      axios.get('https://api.spacexdata.com/v4/dragons')
      .then(function (response) {
        response.data.forEach(function(element) {
          var object = {
            active: element.active,
            crew_cap: element.crew_capacity,
            description: element.description,
            diameter: element.diameter,
            dry_mass_kg: element.dry_mass_kg,
            dry_mass_lb: element.dry_mass_lb,
            first_flight: element.first_flight,
            flickr_images: element.flickr_images,
            heat_shield: element.heat_shield,
            height_w_trunk: element.height_w_trunk,
            launch_payload_mass: element.launch_payload_mass,
            launch_payload_vol: element.launch_payload_vol,
            name: element.name,
            orbit_duration_yr: element.orbit_duration_yr,
            pressurized_capsule: element.pressurized_capsule,
            return_payload_mass: element.return_payload_mass,
            return_payload_vol: element.return_payload_vol,
            sidewall_angle_deg: element.sidewall_angle_deg,
            thrusters: element.thrusters,
            trunk: element.trunk,
            type: element.type,
            wikipedia: element.wikipedia,
            id: element.id,
          }
          that.dragons.push(object)
        })
      })
      .catch(function (error) {
        console.log(error);
      })
      axios.get('https://api.spacexdata.com/v4/landpads')
      .then(function (response) {
        response.data.forEach(function(element) {
          var object = {
            name: element.name,
            full_name: element.full_name,
            status: element.status,
            type: element.type,
            locality: element.locality,
            region: element.region,
            location: element.locality+', '+element.region,
            latitude: element.latitude,
            longitude: element.longitude,
            landing_attempts: element.landing_attempts,
            landing_successes: element.landing_successes,
            landing_attempt_success: element.landing_successes+'/'+element.landing_attempts,
            wikipedia: element.wikipedia,
            details: element.details,
            launches: element.launches,
            id: element.id,
          }
          that.landpads.push(object)
        })
      })
      .catch(function (error) {
        console.log(error);
      })
      axios.get('https://api.spacexdata.com/v4/launches')
      .then(function (response) {
        response.data.forEach(function(element) {
          var object = {
            fairings: element.fairings,
            links: element.links,
            static_fire_date_utc: element.static_fire_date_utc,
            static_fire_date_unix: element.static_fire_date_unix,
            tbd: element.tbd,
            net: element.net,
            window: element.window,
            rocket: element.rocket,
            success: element.success,
            failures: element.failures,
            details: element.details,
            crew: element.crew,
            ships: element.ships,
            capsules: element.capsules,
            payloads: element.payloads,
            launchpad: element.launchpad,
            auto_update: element.auto_update,
            flight_number: element.flight_number,
            name: element.name,
            date_utc: element.date_utc,
            date_unix: element.date_unix,
            date_local: element.date_local,
            date_precision: element.date_precision,
            upcoming: element.upcoming,
            cores: element.cores,
            id: element.id,
          }
          that.launches.push(object)
        })
      })
      .catch(function (error) {
        console.log(error);
      })
      axios.get('https://api.spacexdata.com/v4/launchpads')
      .then(function (response) {
        response.data.forEach(function(element) {
          var object = {
            name: element.name,
            full_name: element.full_name,
            locality: element.locality,
            region: element.region,
            timezone: element.timezone,
            latitude: element.latitude,
            longitude: element.longitude,
            launch_attempts: element.launch_attempts,
            launch_successes: element.launch_successes,
            launch_success_attempt: element.launch_successes+'/'+element.launch_attempts,
            rockets: element.rockets,
            launches: element.launches,
            status: element.status,
            id: element.id,
          }
          that.launchpads.push(object)
        })
      })
      .catch(function (error) {
        console.log(error);
      })
      axios.get('https://api.spacexdata.com/v4/payloads')
      .then(function (response) {
        response.data.forEach(function(element) {
          var object = {
            dragon: element.dragon,
            name: element.name,
            type: element.type,
            reused: element.reused,
            launch: element.launch,
            customers: element.customers,
            customers_string: "",
            norad_ids: element.norad_ids,
            nationalities: element.nationalities,
            nationalities_string: "",
            manufacturers: element.manufacturers,
            mass_kg: element.mass_kg,
            mass_lbs: element.mass_lbs,
            orbit: element.orbit,
            reference_system: element.reference_system,
            regime: element.regime,
            longitude: element.longitude,
            semi_major_axis_km: element.semi_major_axis_km,
            eccentricity: element.eccentricity,
            periapsis_km: element.periapsis_km,
            apoapsis_km: element.apoapsis_km,
            inclination_deg: element.inclination_deg,
            period_min: element.period_min,
            lifespan_years: element.lifespan_years,
            epoch: element.epoch,
            mean_motion: element.mean_motion,
            raan: element.raan,
            arg_of_pericenter: element.arg_of_pericenter,
            mean_anomaly: element.mean_anomaly,
            id: element.id,
          }
          
          var cust_string = ""
          object.customers.forEach(function(element, index) {
            if(index == 0) {
              cust_string = cust_string+element
            } else {
              cust_string = cust_string+", "+element
            }   
          })
          object.customers_string = cust_string

          var nat_string = ""
          object.nationalities.forEach(function(element, index) {
            if(index == 0) {
              nat_string = nat_string+element
            } else {
              nat_string = nat_string+", "+element
            }   
          })
          object.nationalities_string = nat_string

          that.payloads.push(object)
        })
      })
      .catch(function (error) {
        console.log(error);
      })
      axios.get('https://api.spacexdata.com/v4/fairings')
      .then(function (response) {
        response.data.forEach(function(element) {
          var object = {
            serial: element.serial,
            version: element.version,
            status: element.status,
            reuse_count: element.reuse_count,
            net_landing_attempts: element.net_landing_attempts,
            net_landing: element.net_landing,
            net_landing_success_attempts: element.net_landing+'/'+element.net_landing_attempts,
            water_landing_attempts: element.water_landing_attempts,
            water_landing: element.water_landing,
            water_landing_success_attempts: element.water_landing+'/'+element.water_landing_attempts,
            last_update: element.last_update,
            launches: element.launches
          }
          that.fairings.push(object)
        })
      })
      .catch(function (error) {
        console.log(error);
      })
      axios.get('https://api.spacexdata.com/v4/rockets')
      .then(function (response) {
        response.data.forEach(function(element) {
          that.rockets.push(element)
        })
      })
      .catch(function (error) {
        console.log(error);
      })
      axios.get('https://api.spacexdata.com/v4/ships')
      .then(function (response) {
        response.data.forEach(function(element) {
          that.ships.push(element)
        })
      })
      .catch(function (error) {
        console.log(error);
      })
      axios.get('https://api.spacexdata.com/v4/starlink')
      .then(function (response) {
        response.data.forEach(function(element) {
          that.starlinks.push(element)
        })
      })
      .catch(function (error) {
        console.log(error);
      })
    }
  },
}
</script>
