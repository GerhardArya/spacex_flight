<template>
  <v-row justify="center" align="center">
    <v-col cols="12">
      <v-row justify="start" align="center">
    		<v-col cols="3">
					<b>ID:</b>
				</v-col>
				<v-col cols="7">
					<v-text-field
            v-model="dragon_id"
            solo
						hide-details
          ></v-text-field>
				</v-col>
				<v-col cols="2">
					<v-btn @click="loadDragon">Search</v-btn>
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
            				:value="dragon_name"
            				solo
            				readonly
										hide-details
          				></v-text-field>
								</v-col>
							</v-row>
							<v-row justify="start" align="center">
								<v-col cols="4">
									<b>Type:</b>
								</v-col>
								<v-col cols="8">
									<v-text-field
            				:value="dragon_type"
            				solo
            				readonly
										hide-details
          				></v-text-field>
								</v-col>
							</v-row>
							<v-row justify="start" align="center">
								<v-col cols="4">
									<b>Status:</b>
								</v-col>
								<v-col cols="8">
									<v-text-field
            				:value="dragon_status"
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
  								:src="dragon_photo"
								></v-img>
							</v-row>
						</v-col>
					</v-row>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>First Flight:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="dragon_first_flight"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Crew Capacity:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="dragon_crew_capacity"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Orbit Duration:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="dragon_orbit_duration"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Height with Trunk (m):</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="dragon_height_trunk"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Diameter (m):</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="dragon_diameter"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Side Wall Angle (deg):</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="dragon_sidewall_angle"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Dry Mass (kg):</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="dragon_dry_mass"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Launch Payload Mass (kg):</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="dragon_launch_payload_mass"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Launch Payload Volume (m3):</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="dragon_launch_payload_vol"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Return Payload Mass (kg):</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="dragon_return_payload_mass"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Return Payload Volume (m3):</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="dragon_return_payload_vol"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Pressurized Capsule Payload Volume (m3):</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="dragon_pressurized_capsule_payload_vol"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Trunk Volume (m3):</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="dragon_trunk_vol"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Trunk Cargo:</b>
				</v-col>
				<v-col cols="9">
					<v-textarea
						:value="dragon_trunk_cargo"
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
					<b>Heatshield:</b>
				</v-col>
				<v-col cols="9">
					<v-textarea
						:value="dragon_heatshield"
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
					<b>Thrusters:</b>
				</v-col>
				<v-col cols="9">
					<v-textarea
						:value="dragon_thrusters"
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
					<b>Description:</b>
				</v-col>
				<v-col cols="9">
					<v-textarea
						:value="dragon_description"
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
				<v-col cols="9">
					<v-text-field
            :value="dragon_wiki"
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
	name: 'DragonInfo',
	components: {
		
	},
	data() {
		return {
			dragon_id: '',
			dragon_name: '',
			dragon_type: '',
			dragon_status: '',
			dragon_photo: require('@/assets/image_placeholder.png'),
			photoWidth: 0,
			dragon_first_flight: '',
			dragon_crew_capacity: '',
			dragon_orbit_duration: '',
			dragon_height_trunk: '',
			dragon_diameter: '',
			dragon_sidewall_angle: '',
			dragon_dry_mass: '',
			dragon_launch_payload_mass: '',
			dragon_launch_payload_vol: '',
			dragon_return_payload_mass: '',
			dragon_return_payload_vol: '',
			dragon_pressurized_capsule_payload_vol: '',
			dragon_trunk_vol: '',
			dragon_trunk_cargo: [],
			dragon_heatshield: [],
			dragon_thrusters: [],
			dragon_description: '',
			dragon_wiki: ''
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
		if(Object.keys(this.$route.params).length > 0){
			if(this.$route.params.type === 'dragon') {
				axios.get('https://api.spacexdata.com/v4/dragons/'+this.$route.params.id)
      	.then(function (response) {
					that.dragon_id = response.data.id
					that.dragon_name = response.data.name
					that.dragon_type = response.data.type
					that.dragon_status = (response.data.active) ? 'active' : 'inactive'
					that.dragon_photo = response.data.flickr_images[0]
					that.dragon_first_flight = response.data.first_flight
					that.dragon_crew_capacity = response.data.crew_capacity
					that.dragon_orbit_duration = response.data.orbit_duration_yr
					that.dragon_height_trunk = response.data.height_w_trunk.meters
					that.dragon_diameter = response.data.diameter.meters
					that.dragon_sidewall_angle = response.data.sidewall_angle_deg
					that.dragon_dry_mass = response.data.dry_mass_kg
					that.dragon_launch_payload_mass = response.data.launch_payload_mass.kg
					that.dragon_launch_payload_vol = response.data.launch_payload_vol.cubic_meters
					that.dragon_return_payload_mass = response.data.return_payload_mass.kg
					that.dragon_return_payload_vol = response.data.return_payload_vol.cubic_meters
					that.dragon_pressurized_capsule_payload_vol = response.data.pressurized_capsule.payload_volume.cubic_meters
					that.dragon_trunk_vol = response.data.trunk.trunk_volume.cubic_meters
					that.dragon_trunk_cargo = JSON.stringify(response.data.trunk.cargo, null, 2)
					that.dragon_heatshield = JSON.stringify(response.data.heat_shield, null, 2)
					that.dragon_thrusters = JSON.stringify(response.data.thrusters, null, 2)
					that.dragon_description = response.data.description
					that.dragon_wiki = response.data.wikipedia
      	})
      	.catch(function (error) {
        	console.log(error);
      	})
			}
		}
	},
	methods: {
		resizeHandler(){
			this.photoWidth = (document.getElementById('detailMain').getBoundingClientRect().width)*0.25-31.875
    },
    loadDragon() {
			var that = this
			axios.get('https://api.spacexdata.com/v4/dragons/'+this.dragon_id)
      .then(function (response) {
				that.dragon_name = response.data.name
				that.dragon_type = response.data.type
				that.dragon_status = (response.data.active) ? 'active' : 'inactive'
				that.dragon_photo = response.data.flickr_images[0]
				that.dragon_first_flight = response.data.first_flight
				that.dragon_crew_capacity = response.data.crew_capacity
				that.dragon_orbit_duration = response.data.orbit_duration_yr
				that.dragon_height_trunk = response.data.height_w_trunk.meters
				that.dragon_diameter = response.data.diameter.meters
				that.dragon_sidewall_angle = response.data.sidewall_angle_deg
				that.dragon_dry_mass = response.data.dry_mass_kg
				that.dragon_launch_payload_mass = response.data.launch_payload_mass.kg
				that.dragon_launch_payload_vol = response.data.launch_payload_vol.cubic_meters
				that.dragon_return_payload_mass = response.data.return_payload_mass.kg
				that.dragon_return_payload_vol = response.data.return_payload_vol.cubic_meters
				that.dragon_pressurized_capsule_payload_vol = response.data.pressurized_capsule.payload_volume.cubic_meters
				that.dragon_trunk_vol = response.data.trunk.trunk_volume.cubic_meters
				that.dragon_trunk_cargo = JSON.stringify(response.data.trunk.cargo, null, 2)
				that.dragon_heatshield = JSON.stringify(response.data.heat_shield, null, 2)
				that.dragon_thrusters = JSON.stringify(response.data.thrusters, null, 2)
				that.dragon_description = response.data.description
				that.dragon_wiki = response.data.wikipedia
      })
      .catch(function (error) {
        console.log(error);
      })
		}
	},
}
</script>