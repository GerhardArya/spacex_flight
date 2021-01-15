<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <v-card>
        <v-card-title class="headline">
          SpaceX Insight
        </v-card-title>
        <v-img
          src="https://live.staticflickr.com/65535/50618463487_d05aef1611_3k.jpg"
          height="250px"
        ></v-img>
        <v-card-text>
          <p>A web application made to provide some insight on SpaceX and their flight data available through <a target="_blank" href="https://github.com/r-spacex/SpaceX-API/tree/master/docs/v4">this public API</a>.</p>
          <h2>Company Summary: </h2>
          <p>{{ company_info.summary }}</p>
          <h2>Important Information: </h2>
          <div><b>CEO:</b> {{ company_info.ceo }}</div>
          <div><b>CTO:</b> {{ company_info.cto }}</div>
          <div><b>COO:</b> {{ company_info.coo }}</div>
          <p><b>CTO (Propulsion):</b> {{ company_info.cto_propulsion }}</p>
          <div><b>Founder:</b> {{ company_info.founder }}</div>
          <div><b>Founded:</b> {{ company_info.founded }}</div>
          <div><b>Employees:</b> {{ company_info.employees }}</div>
          <div><b>Valuation:</b> {{ company_info.valuation }}</div>
          <p><b>Address:</b> {{ company_info.headquarters.address }}, {{ company_info.headquarters.city }}, {{ company_info.headquarters.state }}</p>
          <div><b>Vehicles:</b> {{ company_info.vehicles }}</div>
          <div><b>Test Sites:</b> {{ company_info.test_sites }}</div>
          <p><b>Launch Sites:</b> {{ company_info.launch_sites }}</p>
          <div>
            <b>Links: </b>
            <a target="_blank" :href="company_info.links.website">
              <v-icon size="18px">{{ 'mdi-web' }}</v-icon>
            </a>
            <a target="_blank" :href="company_info.links.flickr">
              <v-icon size="18px">{{ 'mdi-image' }}</v-icon>
            </a>
            <a target="_blank" :href="company_info.links.twitter">
              <v-icon size="18px">{{ 'mdi-twitter' }}</v-icon>
            </a>
            <a target="_blank" :href="company_info.links.elon_twitter">
              <v-icon size="18px">{{ 'mdi-twitter' }}</v-icon>
            </a>
          </div>
        </v-card-text>
      </v-card>
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
      title: "Home"
    };
  },
  data () {
    return {
      company_info:{
        headquarters: '',
        links: '',
        name: '',
        founder: '',
        founded: '',
        employees: '',
        vehicles: '',
        launch_sites: '',
        test_sites: '',
        ceo: '',
        cto: '',
        coo: '',
        cto_propulsion: '',
        valuation: '',
        summary: '',
        id: '',
      },
    }
  },
  mounted(){
    this.init()
  },
  methods:{
    init(){
      var that = this
      axios.get('https://api.spacexdata.com/v4/company')
      .then(function (response) {
        that.company_info = response.data
        var temp = parseInt(that.company_info.valuation);
        var formatter = new Intl.NumberFormat('en-US', {
          style: 'currency',
          currency: 'USD',
        });
        that.company_info.valuation = formatter.format(temp);
      })
      .catch(function (error) {
        console.log(error);
      })
    }
  },
}
</script>
