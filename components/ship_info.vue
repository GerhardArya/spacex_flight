<template>
  <v-row justify="center" align="center">
    <v-col cols="12">
      <v-row justify="start" align="center">
    		<v-col cols="3">
					<b>ID:</b>
				</v-col>
				<v-col cols="7">
					<v-text-field
            v-model="ship_id"
            solo
						hide-details
          ></v-text-field>
				</v-col>
				<v-col cols="2">
					<v-btn @click="loadShip">Search</v-btn>
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
            				:value="ship_name"
            				solo
            				readonly
										hide-details
          				></v-text-field>
								</v-col>
							</v-row>
							<v-row justify="start" align="center">
								<v-col cols="4">
									<b>Legacy ID:</b>
								</v-col>
								<v-col cols="8">
									<v-text-field
            				:value="ship_legacy_id"
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
            				:value="ship_type"
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
  								:src="ship_photo"
								></v-img>
							</v-row>
						</v-col>
					</v-row>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Model:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="ship_model"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Year Built:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="ship_year_built"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Home Port:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="ship_home_port"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Mass (kg):</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="ship_mass_kg"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Speed (kn):</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="ship_speed_kn"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Course (deg):</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="ship_course_deg"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Latitude:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="ship_latitude"
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
            :value="ship_longitude"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Active:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="ship_active"
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
            :value="ship_status"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Roles</b>
				</v-col>
				<v-col cols="9">
					<v-textarea
						:value="ship_roles"
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
					<b>Launches</b>
				</v-col>
				<v-col cols="9">
					<v-textarea
						:value="ship_launches"
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
					<b>IMO:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="ship_imo"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>MMSI:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="ship_mmsi"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>ABS:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="ship_abs"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>CLASS:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="ship_class"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Last AIS Update:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="ship_last_ais_update"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Link:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="ship_link"
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
			ship_id: '',
			ship_name: '',
			ship_legacy_id: '',
			ship_type: '',
			ship_photo: require('@/assets/image_placeholder.png'),
			photoWidth: 0,
			ship_model: '',
			ship_year_built: '',
			ship_home_port: '',
			ship_mass_kg: '',
			ship_speed_kn: '',
			ship_course_deg: '',
			ship_latitude: '',
			ship_longitude: '',
			ship_active: '',
			ship_status: '',
			ship_roles: [],
			ship_launches: [],
			ship_imo: '',
			ship_mmsi: '',
			ship_abs: '',
			ship_class: '',
			ship_last_ais_update: '',
			ship_link: '',
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
			if(this.$route.params.type === 'ship') {
				axios.get('https://api.spacexdata.com/v4/ships/'+this.$route.params.id)
      	.then(function (response) {
					that.ship_id = response.data.id
					that.ship_name = response.data.name
					that.ship_legacy_id = response.data.legacy_id
					that.ship_type = response.data.type
					that.ship_photo = response.data.image
					that.ship_model = response.data.model
					that.ship_year_built = response.data.year_built
					that.ship_home_port = response.data.home_port
					that.ship_mass_kg = response.data.mass_kg
					that.ship_speed_kn = response.data.speed_kn
					that.ship_course_deg = response.data.course_deg
					that.ship_latitude = response.data.latitude
					that.ship_longitude = response.data.longitude
					that.ship_active = response.data.active
					that.ship_status = response.data.status
					that.ship_roles = response.data.roles
					that.ship_launches = response.data.launches
					that.ship_imo = response.data.imo
					that.ship_mmsi = response.data.mmsi
					that.ship_abs = response.data.abs
					that.ship_class = response.data.class
					that.ship_last_ais_update = response.data.last_ais_update
					that.ship_link = response.data.link
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
    loadShip() {
			var that = this
			axios.get('https://api.spacexdata.com/v4/ships/'+this.ship_id)
      .then(function (response) {
				that.ship_name = response.data.name
				that.ship_legacy_id = response.data.legacy_id
				that.ship_type = response.data.type
				that.ship_photo = response.data.image
				that.ship_model = response.data.model
				that.ship_year_built = response.data.year_built
				that.ship_home_port = response.data.home_port
				that.ship_mass_kg = response.data.mass_kg
				that.ship_speed_kn = response.data.speed_kn
				that.ship_course_deg = response.data.course_deg
				that.ship_latitude = response.data.latitude
				that.ship_longitude = response.data.longitude
				that.ship_active = response.data.active
				that.ship_status = response.data.status
				that.ship_roles = response.data.roles
				that.ship_launches = response.data.launches
				that.ship_imo = response.data.imo
				that.ship_mmsi = response.data.mmsi
				that.ship_abs = response.data.abs
				that.ship_class = response.data.class
				that.ship_last_ais_update = response.data.last_ais_update
				that.ship_link = response.data.link
      })
      .catch(function (error) {
        console.log(error);
      })
		}
	},
}
</script>