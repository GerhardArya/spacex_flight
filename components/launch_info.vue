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
  								:max-width="photoWidth"
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
				<v-col cols="9" class="px-3 py-2">
					<a :href="launch_launchpad.link">{{ launch_launchpad.id }}</a>
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
			<v-row justify="start" align="top">
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
				<v-col cols="9" class="px-3 py-2">
						<a :href="launch_rocket.link">{{ launch_rocket.id }}</a>
				</v-col>
			</v-row>
			<v-row justify="start" align="top">
    		<v-col cols="3">
					<b>Crew:</b>
				</v-col>
				<v-col cols="9">
					<v-row v-for="item in launch_crew" class="px-3 py-2">
						<a :href="item.link">{{ item.id }}</a>
					</v-row>
				</v-col>
			</v-row>
			<v-row justify="start" align="top">
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
			<v-row justify="start" align="top">
    		<v-col cols="3">
					<b>Capsule:</b>
				</v-col>
				<v-col cols="9">
					<v-row v-for="item in launch_capsule" class="px-3 py-2">
						<a :href="item.link">{{ item.id }}</a>
					</v-row>
				</v-col>
			</v-row>
			<v-row justify="start" align="top">
    		<v-col cols="3">
					<b>Payload:</b>
				</v-col>
				<v-col cols="9">
					<v-row v-for="item in launch_payloads" class="px-3 py-2">
						<a :href="item.link">{{ item.id }}</a>
					</v-row>
				</v-col>
			</v-row>
			<v-row justify="start" align="top">
    		<v-col cols="3">
					<b>Core:</b>
				</v-col>
				<v-col cols="9">
					<v-row v-for="item in launch_core" class="px-3 py-2">
						<a :href="item.link">{{ item.id }}</a>
					</v-row>
				</v-col>
			</v-row>
			<v-row justify="start" align="top">
    		<v-col cols="3">
					<b>Landpad:</b>
				</v-col>
				<v-col cols="9">
					<v-row v-for="item in launch_landpad" class="px-3 py-2">
						<a :href="item.link">{{ item.id }}</a>
					</v-row>
				</v-col>
			</v-row>
			<v-row justify="start" align="top">
    		<v-col cols="3">
					<b>Ship:</b>
				</v-col>
				<v-col cols="9">
					<v-row v-for="item in launch_ship" class="px-3 py-2">
						<a :href="item.link">{{ item.id }}</a>
					</v-row>
				</v-col>
			</v-row>
			<v-row justify="start" align="top">
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
					<v-row v-for="item in launch_links" class="px-3 py-2" style="display:inline">
						<a :href="item.link" target="_blank" v-if="item.type === 'wikipedia'">
							<v-icon size="20px">{{ 'mdi-wikipedia' }}</v-icon>
						</a>
						<a :href="item.link" target="_blank" v-else-if="item.type === 'youtube'">
							<v-icon size="20px">{{ 'mdi-youtube' }}</v-icon>
						</a>
						<a :href="item.link" target="_blank" v-if="item.type === 'article'">
							<v-icon size="20px">{{ 'mdi-cellphone-text' }}</v-icon>
						</a>
						<a :href="item.link" target="_blank" v-if="item.type === 'press'">
							<v-icon size="20px">{{ 'mdi-newspaper-variant' }}</v-icon>
						</a>
					</v-row>
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
			photoWidth: 0,
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
			launch_core_raw: '',
			launch_landpad: [],
			launch_ship: [],
			launch_details: '',
			launch_links: [],
			launch_auto_update: '',
		}
	},
	created() {
		this.photoWidth = (document.getElementById('detailMain').getBoundingClientRect().width)*0.25-31.875
    window.addEventListener("resize", this.resizeHandler);
  },
  destroyed() {
    window.removeEventListener("resize", this.resizeHandler);
  },
	mounted(){
		var that = this
		if(Object.keys(that.$route.params).length > 0){
			if(that.$route.params.type === 'launch') {
				that.launch_id = that.$route.params.id
				that.loadLaunch()
			}
		} else if(Object.keys(that.$route.query).length > 0){
			if(that.$route.query.type === 'launch') {
				that.launch_id = that.$route.query.id
				that.loadLaunch()
			}
		}
	},
	methods: {
		resizeHandler(){
			this.photoWidth = (document.getElementById('detailMain').getBoundingClientRect().width)*0.25-31.875
    },
    loadLaunch() {
			var that = this
			axios.get('https://api.spacexdata.com/v4/launches/'+this.launch_id)
      .then(function (response) {
				that.launch_name = response.data.name
				that.launch_flight_number = response.data.flight_number
				that.launch_upcoming = response.data.upcoming
				that.launch_photo = (response.data.links.flickr.original.length > 0) ? response.data.links.flickr.original[0] : require('@/assets/image_placeholder.png')
				that.launch_launchpad = {
					id: response.data.launchpad,
					link: "/details?id="+response.data.launchpad+"&type=launchpad"
				}
				that.launch_date = response.data.date_utc
				that.launch_static_fire_date = response.data.static_fire_date_utc
				that.launch_success = response.data.success
				that.launch_failures = JSON.stringify(response.data.failures, null, 2)
				that.launch_tbd = response.data.tdb
				that.launch_net = response.data.net
				that.launch_window = response.data.window
				that.launch_rocket = {
					id: response.data.rocket,
					link: "/details?id="+response.data.rocket+"&type=rocket"
				}
				response.data.crew.forEach(crewID => {
					that.launch_crew.push({
						id: crewID,
						link: "/details?id="+crewID+"&type=crew"
					})
				});
				that.launch_fairing = JSON.stringify(response.data.fairings, null, 2)
				response.data.capsules.forEach(capsuleID => {
					that.launch_capsule.push({
						id: capsuleID,
						link: "/details?id="+capsuleID+"&type=capsule"
					})
				});
				response.data.payloads.forEach(payloadID => {
					that.launch_payloads.push({
						id: payloadID,
						link: "/details?id="+payloadID+"&type=payload"
					})
				});
				response.data.cores.forEach(element => {
					that.launch_core.push({
						id: element.core,
						link: "/details?id="+element.core+"&type=core"
					})
					that.launch_landpad.push({
						id: element.landpad,
						link: "/details?id="+element.landpad+"&type=landpad"
					})
				})
				that.launch_core_raw = JSON.stringify(response.data.cores, null, 2)
				response.data.ships.forEach(shipID => {
					that.launch_ship.push({
						id: shipID,
						link: "/details?id="+shipID+"&type=ship"
					})
				});
				that.launch_details = response.data.details
				that.launch_links.push({
					type: "wikipedia",
					link: response.data.links.wikipedia
				})
				that.launch_links.push({
					type: "youtube",
					link: response.data.links.webcast
				})
				that.launch_links.push({
					type: "article",
					link: response.data.links.article
				})
				that.launch_links.push({
					type: "press",
					link: response.data.links.presskit
				})
				that.launch_auto_update = response.data.auto_update
      })
      .catch(function (error) {
        console.log(error);
      })
		}
	},
}
</script>