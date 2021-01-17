<template>
  <v-row justify="center" align="center">
    <v-col cols="12">
      <v-row justify="start" align="center">
    		<v-col cols="3">
					<b>ID:</b>
				</v-col>
				<v-col cols="7">
					<v-text-field
            v-model="payload_id"
            solo
						hide-details
          ></v-text-field>
				</v-col>
				<v-col cols="2">
					<v-btn @click="loadPayload">Search</v-btn>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Name:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="payload_name"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Type:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="payload_type"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Launch:</b>
				</v-col>
				<v-col cols="9" class="px-3 py-2">
					<a :href="payload_launch.link">{{ payload_launch.id }}</a>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Lifespan (yr):</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="payload_lifespan_years"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
				<v-col cols="12">
					<b>Dragon:</b>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>Capsule:</b>
				</v-col>
				<v-col cols="9" class="px-3 py-2">
					<a :href="payload_dragon_capsule.link">{{ payload_dragon_capsule.id }}</a>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>Mass Returned (kg):</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="payload_dragon_mass_returned"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>Flight Time (s):</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="payload_dragon_flight_time"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>Manifest:</b>
				</v-col>
				<v-col cols="9" class="px-3 py-2">
					<a :href="payload_dragon_manifest" target="_blank" v-if="payload_dragon_manifest !== ''">
						<v-icon size="20px">{{ 'mdi-web' }}</v-icon>
					</a>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>Landing Type:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="payload_dragon_landing_type"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Reused:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="payload_reused"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="top">
    		<v-col cols="3">
					<b>Customers:</b>
				</v-col>
				<v-col cols="9">
					<v-textarea
						:value="payload_customers"
						height="144"
          	solo
            readonly
						no-resize
						hide-details
        	></v-textarea>
				</v-col>
			</v-row>
			<v-row justify="start" align="top">
    		<v-col cols="3">
					<b>Manufacturers:</b>
				</v-col>
				<v-col cols="9">
					<v-textarea
						:value="payload_manufacturers"
						height="144"
          	solo
            readonly
						no-resize
						hide-details
        	></v-textarea>
				</v-col>
			</v-row>
			<v-row justify="start" align="top">
    		<v-col cols="3">
					<b>Nationalities:</b>
				</v-col>
				<v-col cols="9">
					<v-textarea
						:value="payload_nationalities"
						height="144"
          	solo
            readonly
						no-resize
						hide-details
        	></v-textarea>
				</v-col>
			</v-row>
			<v-row justify="start" align="top">
    		<v-col cols="3">
					<b>NORAD IDs:</b>
				</v-col>
				<v-col cols="9">
					<v-textarea
						:value="payload_norad_ids"
						height="144"
          	solo
            readonly
						no-resize
						hide-details
        	></v-textarea>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Mass (kg):</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="payload_mass_kg"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Orbit:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="payload_orbit"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Reference System:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="payload_reference_system"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Regime:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="payload_regime"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Longitude:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="payload_longitude"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Semi Major Axis (km):</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="payload_semi_major_axis_km"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Eccentricity:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="payload_eccentricity"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Periapsis (km):</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="payload_periapsis_km"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Apoapsis (km):</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="payload_apoapsis_km"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Inclination (deg):</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="payload_inclination_deg"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Period (min):</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="payload_period_min"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Mean Motion:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="payload_mean_motion"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Mean Anomaly:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="payload_mean_anomaly"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Arg of Pericenter:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="payload_arg_of_pericenter"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>RAAN:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="payload_raan"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Epoch:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="payload_epoch"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
    </v-col>
  </v-row>
</template>

<script>
const axios = require('axios');
export default {
	name: 'PayloadInfo',
	components: {
		
	},
	data() {
		return {
			payload_id: '',
			payload_name: '',
			payload_type: '',
			payload_launch: '',
			payload_lifespan_years: '',
			payload_dragon_capsule: '',
			payload_dragon_mass_returned: '',
			payload_dragon_flight_time: '',
			payload_dragon_manifest: '',
			payload_dragon_landing_type: '',
			payload_reused: '',
			payload_customers: [],
			payload_manufacturers: [],
			payload_nationalities: [],
			payload_norad_ids: [],
			payload_mass_kg: '',
			payload_orbit: '',
			payload_reference_system: '',
			payload_regime: '',
			payload_longitude: '',
			payload_semi_major_axis_km: '',
			payload_eccentricity: '',
			payload_periapsis_km: '',
			payload_apoapsis_km: '',
			payload_inclination_deg: '',
			payload_period_min: '',
			payload_mean_motion: '',
			payload_mean_anomaly: '',
			payload_arg_of_pericenter: '',
			payload_raan: '',
			payload_epoch: '',
		}
	},
	mounted(){
		var that = this
		if(Object.keys(that.$route.params).length > 0){
			if(that.$route.params.type === 'payload') {
				that.payload_id = that.$route.params.id
				that.loadPayload()
			}
		} else if(Object.keys(that.$route.query).length > 0){
			if(that.$route.query.type === 'payload') {
				that.payload_id = that.$route.query.id
				that.loadPayload()
			}
		}
	},
	methods: {
    loadPayload() {
			var that = this
			axios.get('https://api.spacexdata.com/v4/payloads/'+this.payload_id)
      .then(function (response) {
				that.payload_name = response.data.name
				that.payload_type = response.data.type
				that.payload_launch = {
					id: response.data.launch,
					link: "/details?id="+response.data.launch+"&type=launch"
				}
				that.payload_lifespan_years = response.data.lifespan_years
				that.payload_dragon_capsule = {
					id: response.data.dragon.capsule,
					link: "/details?id="+response.data.dragon.capsule+"&type=capsule"
				}
				that.payload_dragon_mass_returned = response.data.dragon.mass_returned_kg
				that.payload_dragon_flight_time = response.data.dragon.flight_time_sec
				if(response.data.dragon.manifest) {
					that.payload_dragon_manifest = response.data.dragon.manifest
				}
				if(response.data.dragon.water_landing) {
					that.payload_dragon_landing_type = "Water"
				} else if(response.data.dragon.land_landing) {
					that.payload_dragon_landing_type = "Water"
				}
				that.payload_reused = response.data.reused
				that.payload_customers = response.data.customers
				that.payload_manufacturers = response.data.manufacturers
				that.payload_nationalities = response.data.nationalities
				that.payload_norad_ids = response.data.norad_ids
				that.payload_mass_kg = response.data.mass_kg
				that.payload_orbit = response.data.orbit
				that.payload_reference_system = response.data.reference_system
				that.payload_regime = response.data.regime
				that.payload_longitude = response.data.longitude
				that.payload_semi_major_axis_km = response.data.semi_major_axis_km
				that.payload_eccentricity = response.data.eccentricity
				that.payload_periapsis_km = response.data.periapsis_km
				that.payload_apoapsis_km = response.data.apoapsis_km
				that.payload_inclination_deg = response.data.inclination_deg
				that.payload_period_min = response.data.period_min
				that.payload_mean_motion = response.data.mean_motion
				that.payload_mean_anomaly = response.data.mean_anomaly
				that.payload_arg_of_pericenter = response.data.arg_of_pericenter
				that.payload_raan = response.data.raan
				that.payload_epoch = response.data.epoch
      })
      .catch(function (error) {
        console.log(error);
      })
		}
	},
}
</script>