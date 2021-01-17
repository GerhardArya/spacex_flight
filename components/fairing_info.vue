<template>
  <v-row justify="center" align="center">
    <v-col cols="12">
      <v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Serial:</b>
				</v-col>
				<v-col cols="7">
					<v-text-field
            v-model="fairing_serial"
            solo
						hide-details
          ></v-text-field>
				</v-col>
				<v-col cols="2">
					<v-btn @click="loadFairing">Search</v-btn>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Version:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="fairing_version"
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
            :value="fairing_status"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Reuse Count:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="fairing_reuse"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Net Landing Attempts:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="fairing_net_landing_attempts"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Net Landing Successes:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="fairing_net_landing_successes"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Water Landing Attempts:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="fairing_water_landing_attempts"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Water Landing Successes:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="fairing_water_landing_successes"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="top">
    		<v-col cols="3">
					<b>Launches:</b>
				</v-col>
				<v-col cols="9">
					<v-row v-for="item in fairing_launches" class="px-3 py-2">
						<a :href="item.link">{{ item.id }}</a>
					</v-row>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Last Update:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="fairing_last_update"
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
	name: 'LaunchpadMap',
	components: {
		
	},
	data() {
		return {
			fairing_serial: '',
			fairing_version: '',
			fairing_status: '',
			fairing_reuse: '',
			fairing_net_landing_attempts: '',
			fairing_net_landing_successes: '',
			fairing_water_landing_attempts: '',
			fairing_water_landing_successes: '',
			fairing_launches: '',
			fairing_last_update: '',
		}
	},
	mounted(){
		var that = this
		if(Object.keys(that.$route.params).length > 0){
			if(that.$route.params.type === 'fairing') {
				that.fairing_serial = that.$route.params.id
				that.loadFairing()
			}
		} else if(Object.keys(that.$route.query).length > 0){
			if(that.$route.query.type === 'fairing') {
				that.fairing_serial = that.$route.query.id
				that.loadFairing()
			}
		}
	},
	methods: {
    loadFairing() {
			var that = this
			axios.get('https://api.spacexdata.com/v4/fairings/'+this.fairing_serial)
      .then(function (response) {
				that.fairing_version = response.data.version
				that.fairing_status = response.data.status
				that.fairing_reuse = response.data.reuse_count
				that.fairing_net_landing_attempts = response.data.net_landing_attempts
				that.fairing_net_landing_successes = response.data.net_landing
				that.fairing_water_landing_attempts = response.data.water_landing_attempts
				that.fairing_water_landing_successes = response.data.water_landing
				response.data.launches.forEach(launchID => {
					that.fairing_launches.push({
						id: launchID,
						link: "/details?id="+launchID+"&type=launch"
					})
				});
				that.fairing_last_update = response.data.last_update
      })
      .catch(function (error) {
        console.log(error);
      })
		}
	},
}
</script>