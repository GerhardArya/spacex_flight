<template>
  <v-row justify="center" align="center">
    <v-col cols="12">
      <v-row justify="start" align="center">
    		<v-col cols="3">
					<b>ID:</b>
				</v-col>
				<v-col cols="7">
					<v-text-field
            v-model="landpad_id"
            solo
						hide-details
          ></v-text-field>
				</v-col>
				<v-col cols="2">
					<v-btn @click="loadLandpad">Search</v-btn>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Name:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="landpad_name"
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
            :value="landpad_full_name"
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
            :value="landpad_type"
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
            :value="landpad_status"
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
            :value="landpad_locality"
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
            :value="landpad_region"
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
				<v-col cols="9" class="px-3 py-2">
					<a :href="landpad_google_maps" target="_blank" v-if="landpad_google_maps !== ''">
						<v-icon size="20px">{{ 'mdi-google-maps' }}</v-icon>
					</a>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Landing Attempts:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="landpad_landing_attempts"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Landing Successes:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="landpad_landing_successes"
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
					<v-row v-for="item in landpad_launches" class="px-3 py-2">
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
						:value="landpad_details"
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
					<b>Wikipedia:</b>
				</v-col>
				<v-col cols="9" class="px-3 py-2">
					<a :href="landpad_wiki" target="_blank" v-if="landpad_wiki !== ''">
						<v-icon size="20px">{{ 'mdi-wikipedia' }}</v-icon>
					</a>
				</v-col>
			</v-row>
    </v-col>
  </v-row>
</template>

<script>
const axios = require('axios');
export default {
	name: 'LandpadMap',
	components: {
		
	},
	data() {
		return {
			landpad_id: '',
			landpad_name: '',
			landpad_full_name: '',
			landpad_type: '',
			landpad_status: '',
			landpad_locality: '',
			landpad_region: '',
			landpad_google_maps: '',
			landpad_landing_attempts: '',
			landpad_landing_successes: '',
			landpad_launches: [],
			landpad_details: '',
			landpad_wiki: '',
		}
	},
	mounted(){
		var that = this
		if(Object.keys(that.$route.params).length > 0){
			if(that.$route.params.type === 'landpad') {
				that.landpad_id = that.$route.params.id
				that.loadLandpad()
			}
		} else if(Object.keys(that.$route.query).length > 0){
			if(that.$route.query.type === 'landpad') {
				that.landpad_id = that.$route.query.id
				that.loadLandpad()
			}
		}
	},
	methods: {
    loadLandpad() {
			var that = this
			axios.get('https://api.spacexdata.com/v4/landpads/'+this.landpad_id)
      .then(function (response) {
				that.landpad_name = response.data.name
				that.landpad_full_name = response.data.full_name
				that.landpad_type = response.data.type
				that.landpad_status = response.data.status
				that.landpad_locality = response.data.locality
				that.landpad_region = response.data.region
				that.landpad_google_maps = "https://www.google.com/maps/@?api=1&map_action=map&basemap=satellite&center="+response.data.latitude+","+response.data.longitude
				that.landpad_landing_attempts = response.data.landing_attempts
				that.landpad_landing_successes = response.data.landing_successes
				response.data.launches.forEach(launchID => {
					that.landpad_launches.push({
						id: launchID,
						link: "/details?id="+launchID+"&type=launch"
					})
				});
				that.landpad_details = response.data.details
				that.landpad_wiki = response.data.wikipedia
      })
      .catch(function (error) {
        console.log(error);
      })
		}
	},
}
</script>