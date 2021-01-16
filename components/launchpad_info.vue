<template>
  <v-row justify="center" align="center">
    <v-col cols="12">
      <v-row justify="start" align="center">
    		<v-col cols="3">
					<b>ID:</b>
				</v-col>
				<v-col cols="7">
					<v-text-field
            v-model="launchpad_id"
            solo
						hide-details
          ></v-text-field>
				</v-col>
				<v-col cols="2">
					<v-btn @click="loadLaunchpad">Search</v-btn>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Name:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="launchpad_name"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Full Name:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="launchpad_full_name"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Status:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="launchpad_status"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Locality:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="launchpad_locality"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Region:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="launchpad_region"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Google Maps:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="launchpad_google_maps"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Time Zone:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="launchpad_time_zone"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Launch Attempts:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="launchpad_launch_attempts"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Launch Successes:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="launchpad_launch_successes"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Launches:</b>
				</v-col>
				<v-col cols="9">
					<v-textarea
						:value="launchpad_launches"
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
					<b>Rockets:</b>
				</v-col>
				<v-col cols="9">
					<v-textarea
						:value="launchpad_rockets"
						height="144"
          	solo
            readonly
						no-resize
						hide-details
        	></v-textarea>
				</v-col>
			</v-row>
    </v-col>
  </v-row>
</template>

<script>
const axios = require('axios');
export default {
	name: 'LaunchpadMap',
	components: {
		
	},
	data() {
		return {
			launchpad_id: '',
			launchpad_name: '',
			launchpad_full_name: '',
			launchpad_status: '',
			launchpad_locality: '',
			launchpad_region: '',
			launchpad_google_maps: '',
			launchpad_time_zone: '',
			launchpad_launch_attempts: '',
			launchpad_launch_successes: '',
			launchpad_launches: [],
			launchpad_rockets: [],
		}
	},
	mounted(){
		var that = this
		if(Object.keys(this.$route.params).length > 0){
			if(this.$route.params.type === 'launchpad') {
				axios.get('https://api.spacexdata.com/v4/launchpads/'+this.$route.params.id)
      	.then(function (response) {
					that.launchpad_id = response.data.id
					that.launchpad_name = response.data.name
					that.launchpad_full_name = response.data.full_name
					that.launchpad_status = response.data.status
					that.launchpad_locality = response.data.locality
					that.launchpad_region = response.data.region
					that.launchpad_google_maps = "https://www.google.com/maps/@?api=1&map_action=map&basemap=satellite&center="+response.data.latitude+","+response.data.longitude
					that.launchpad_time_zone = response.data.timezone
					that.launchpad_launch_attempts = response.data.launch_attempts
					that.launchpad_launch_successes = response.data.launch_successes
					that.launchpad_launches = response.data.launches
					that.launchpad_rockets = response.data.rockets
      	})
      	.catch(function (error) {
        	console.log(error);
      	})
			}
		}
	},
	methods: {
    loadLaunchpad() {
			var that = this
			axios.get('https://api.spacexdata.com/v4/launchpads/'+this.launchpad_id)
      .then(function (response) {
				that.launchpad_name = response.data.name
				that.launchpad_full_name = response.data.full_name
				that.launchpad_status = response.data.status
				that.launchpad_locality = response.data.locality
				that.launchpad_region = response.data.region
				that.launchpad_google_maps = "https://www.google.com/maps/@?api=1&map_action=map&basemap=satellite&center="+response.data.latitude+","+response.data.longitude
				that.launchpad_time_zone = response.data.timezone
				that.launchpad_launch_attempts = response.data.launch_attempts
				that.launchpad_launch_successes = response.data.launch_successes
				that.launchpad_launches = response.data.launches
				that.launchpad_rockets = response.data.rockets
      })
      .catch(function (error) {
        console.log(error);
      })
		}
	},
}
</script>