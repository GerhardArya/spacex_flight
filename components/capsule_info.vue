<template>
  <v-row justify="center" align="center">
    <v-col cols="12">
      <v-row justify="start" align="center">
    		<v-col cols="3">
					<b>ID:</b>
				</v-col>
				<v-col cols="7">
					<v-text-field
            v-model="capsule_id"
            solo
						hide-details
          ></v-text-field>
				</v-col>
				<v-col cols="2">
					<v-btn @click="loadCapsule">Search</v-btn>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Serial:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="capsule_serial"
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
            :value="capsule_type"
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
            :value="capsule_status"
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
					<v-row v-for="item in capsule_launches" class="px-3 py-2">
						<a :href="item.link">{{ item.id }}</a>
					</v-row>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Land Landings:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="capsule_land_landings"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Water Landings:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="capsule_water_landings"
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
            :value="capsule_reuse"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="top">
    		<v-col cols="3">
					<b>Last update:</b>
				</v-col>
				<v-col cols="9">
					<v-textarea
						:value="capsule_last_update"
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
	name: 'CapsuleInfo',
	components: {
		
	},
	data() {
		return {
			capsule_id: '',
			capsule_serial: '',
			capsule_type: '',
			capsule_status: '',
			capsule_launches: [],
			capsule_land_landings: '',
			capsule_water_landings: '',
			capsule_reuse: '',
			capsule_last_update: ''
		}
	},
	mounted(){
		var that = this
		if(Object.keys(that.$route.params).length > 0){
			if(that.$route.params.type === 'capsule') {
				that.capsule_id = that.$route.params.id
				that.loadCapsule()
			}
		} else if(Object.keys(that.$route.query).length > 0){
			if(that.$route.query.type === 'capsule') {
				that.capsule_id = that.$route.query.id
				that.loadCapsule()
			}
		}
	},
	methods: {
    loadCapsule() {
			var that = this
			axios.get('https://api.spacexdata.com/v4/capsules/'+this.capsule_id)
      .then(function (response) {
				that.capsule_serial = response.data.serial
				that.capsule_type = response.data.type
				that.capsule_status = response.data.status
				response.data.launches.forEach(launchID => {
					that.capsule_launches.push({
						id: launchID,
						link: "/details?id="+launchID+"&type=launch"
					})
				});
				that.capsule_land_landings = response.data.land_landings
				that.capsule_water_landings = response.data.water_landings
				that.capsule_reuse = response.data.reuse_count
				that.capsule_last_update = response.data.last_update
      })
      .catch(function (error) {
        console.log(error);
      })
		}
	},
}
</script>