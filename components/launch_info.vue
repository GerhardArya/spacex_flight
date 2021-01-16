<template>
  <v-row justify="center" align="center">
    <v-col cols="12">
      <v-row justify="start" align="center">
    		<v-col cols="3">
					<b>ID:</b>
				</v-col>
				<v-col cols="7">
					<v-text-field
            v-model="launch_id"
            solo
						hide-details
          ></v-text-field>
				</v-col>
				<v-col cols="2">
					<v-btn @click="loadLaunch">Search</v-btn>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
				<v-col cols="12">
					<v-row justify="start" align="center">
						<v-col cols="9">
							<v-row justify="start" align="center">
								<v-col cols="4">
									<b>Name:</b>
								</v-col>
								<v-col cols="8">
									<v-text-field
            				:value="launch_name"
            				solo
            				readonly
										hide-details
          				></v-text-field>
								</v-col>
							</v-row>
							<v-row justify="start" align="center">
								<v-col cols="4">
									<b>Flight Number:</b>
								</v-col>
								<v-col cols="8">
									<v-text-field
            				:value="launch_flight_number"
            				solo
            				readonly
										hide-details
          				></v-text-field>
								</v-col>
							</v-row>
							<v-row justify="start" align="center">
								<v-col cols="4">
									<b>Upcoming:</b>
								</v-col>
								<v-col cols="8">
									<v-text-field
            				:value="launch_upcoming"
            				solo
            				readonly
										hide-details
          				></v-text-field>
								</v-col>
							</v-row>
						</v-col>
						<v-col cols="3">
							<v-row justify="center" align="center">
								<v-img
  								max-height="160"
  								max-width="200"
  								:src="launch_photo"
								></v-img>
							</v-row>
						</v-col>
					</v-row>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Launchpad:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="launch_launchpad"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Date (UTC):</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="launch_date"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Static Fire Date (UTC):</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="launch_static_fire_date"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Success:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="launch_success"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Failures:</b>
				</v-col>
				<v-col cols="9">
					<v-textarea
						:value="launch_failures"
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
					<b>TBD:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="launch_tbd"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>NET:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="launch_net"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Window:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="launch_window"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Rocket:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="launch_rocket"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Crew:</b>
				</v-col>
				<v-col cols="9">
					<v-textarea
						:value="launch_crew"
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
					<b>Fairing:</b>
				</v-col>
				<v-col cols="9">
					<v-textarea
						:value="launch_fairing"
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
					<b>Capsule:</b>
				</v-col>
				<v-col cols="9">
					<v-textarea
						:value="launch_capsule"
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
					<b>Payload:</b>
				</v-col>
				<v-col cols="9">
					<v-textarea
						:value="launch_payloads"
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
					<b>Core:</b>
				</v-col>
				<v-col cols="9">
					<v-textarea
						:value="launch_core"
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
					<b>Ship:</b>
				</v-col>
				<v-col cols="9">
					<v-textarea
						:value="launch_ship"
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
					<b>Details:</b>
				</v-col>
				<v-col cols="9">
					<v-textarea
						:value="launch_details"
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
					<b>Links:</b>
				</v-col>
				<v-col cols="9">
					<v-textarea
						:value="launch_links"
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
					<b>Auto Update:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="launch_auto_update"
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
	name: 'LaunchInfo',
	components: {
		
	},
	data() {
		return {
			launch_id: '',
			launch_name: '',
			launch_flight_number: '',
			launch_upcoming: '',
			launch_photo: require('@/assets/image_placeholder.png'),
			launch_launchpad: '',
			launch_date: '',
			launch_static_fire_date: '',
			launch_success: '',
			launch_failures: [],
			launch_tbd: '',
			launch_net: '',
			launch_window: '',
			launch_rocket: '',
			launch_crew: [],
			launch_fairing: [],
			launch_capsule: [],
			launch_payloads: [],
			launch_core: [],
			launch_ship: [],
			launch_details: '',
			launch_links: [],
			launch_auto_update: '',
		}
	},
	mounted(){
		var that = this
		if(Object.keys(this.$route.params).length > 0){
			if(this.$route.params.type === 'launch') {
				axios.get('https://api.spacexdata.com/v4/launches/'+this.$route.params.id)
      	.then(function (response) {
					that.launch_id = response.data.id
					that.launch_name = response.data.name
					that.launch_flight_number = response.data.flight_number
					that.launch_upcoming = response.data.upcoming
					that.launch_photo = (response.data.links.flickr.original.length > 0) ? response.data.links.flickr.original[0] : require('@/assets/image_placeholder.png')
					that.launch_launchpad = response.data.launchpad
					that.launch_date = response.data.date_utc
					that.launch_static_fire_date = response.data.static_fire_date_utc
					that.launch_success = response.data.success
					that.launch_failures = JSON.stringify(response.data.failures, null, 2)
					that.launch_tbd = response.data.tdb
					that.launch_net = response.data.net
					that.launch_window = response.data.window
					that.launch_rocket = response.data.rocket
					that.launch_crew = response.data.crew
					that.launch_fairing = JSON.stringify(response.data.fairings, null, 2)
					that.launch_capsule = response.data.capsules
					that.launch_payloads = response.data.payloads
					that.launch_core = JSON.stringify(response.data.cores, null, 2)
					that.launch_ship = response.data.ships
					that.launch_details = response.data.details
					that.launch_links = JSON.stringify(response.data.links, null, 2)
					that.launch_auto_update = response.data.auto_update
      	})
      	.catch(function (error) {
        	console.log(error);
      	})
			}
		}
	},
	methods: {
    loadLaunch() {
			var that = this
			axios.get('https://api.spacexdata.com/v4/launches/'+this.launch_id)
      .then(function (response) {
				that.launch_name = response.data.name
				that.launch_flight_number = response.data.flight_number
				that.launch_upcoming = response.data.upcoming
				that.launch_photo = (response.data.links.flickr.original.length > 0) ? response.data.links.flickr.original[0] : require('@/assets/image_placeholder.png')
				that.launch_launchpad = response.data.launchpad
				that.launch_date = response.data.date_utc
				that.launch_static_fire_date = response.data.static_fire_date_utc
				that.launch_success = response.data.success
				that.launch_failures = JSON.stringify(response.data.failures, null, 2)
				that.launch_tbd = response.data.tdb
				that.launch_net = response.data.net
				that.launch_window = response.data.window
				that.launch_rocket = response.data.rocket
				that.launch_crew = response.data.crew
				that.launch_fairing = JSON.stringify(response.data.fairings, null, 2)
				that.launch_capsule = response.data.capsules
				that.launch_payloads = response.data.payloads
				that.launch_core = JSON.stringify(response.data.cores, null, 2)
				that.launch_ship = response.data.ships
				that.launch_details = response.data.details
				that.launch_links = JSON.stringify(response.data.links, null, 2)
				that.launch_auto_update = response.data.auto_update
      })
      .catch(function (error) {
        console.log(error);
      })
		}
	},
}
</script>