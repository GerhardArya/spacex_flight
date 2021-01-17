<template>
  <v-row justify="center" align="center">
    <v-col cols="12">
      <v-row justify="start" align="center">
    		<v-col cols="3">
					<b>ID:</b>
				</v-col>
				<v-col cols="7">
					<v-text-field
            v-model="rocket_id"
            solo
						hide-details
          ></v-text-field>
				</v-col>
				<v-col cols="2">
					<v-btn @click="loadRocket">Search</v-btn>
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
            				:value="rocket_name"
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
            				:value="rocket_type"
            				solo
            				readonly
										hide-details
          				></v-text-field>
								</v-col>
							</v-row>
							<v-row justify="start" align="center">
								<v-col cols="4">
									<b>Active:</b>
								</v-col>
								<v-col cols="8">
									<v-text-field
            				:value="rocket_active"
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
  								:src="rocket_photo"
								></v-img>
							</v-row>
						</v-col>
					</v-row>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Company:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="rocket_company"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Country:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="rocket_country"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>First Flight:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="rocket_first_flight"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Success Rate (%):</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="rocket_sr"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Cost Per Launch ($):</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="rocket_cost"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Stages:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="rocket_stages"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Boosters:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="rocket_boosters"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Height (m):</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="rocket_height"
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
            :value="rocket_diameter"
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
            :value="rocket_mass"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
				<v-col cols="12">
					<b>First Stage:</b>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>Thrust (Sea Level, kN):</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="rocket_first_stage_thrust_sea_level"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>Thrust (Vacuum, kN):</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="rocket_first_stage_thrust_vacuum"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>Reusable:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="rocket_first_stage_reusable"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>Engines:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="rocket_first_stage_engines"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>Fuel Amount (ton):</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="rocket_first_stage_fuel_amount"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>Burn Time (s):</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="rocket_first_stage_burn_time"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
				<v-col cols="12">
					<b>Second Stage:</b>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>Thrust (kN):</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="rocket_second_stage_thrust"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="top">
    		<v-col cols="3">
					&emsp;
					<b>Payloads:</b>
				</v-col>
				<v-col cols="9">
					<v-textarea
						:value="rocket_second_stage_payloads"
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
					&emsp;
					<b>Reusable:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="rocket_second_stage_reusable"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>Engines:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="rocket_second_stage_engines"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>Fuel Amount (ton):</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="rocket_second_stage_fuel_amount"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>Burn Time (s):</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="rocket_second_stage_burn_time"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
				<v-col cols="12">
					<b>Engines:</b>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>ISP (Sea Level):</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="rocket_engines_isp_sea_level"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>ISP (Vacuum):</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="rocket_engines_isp_vacuum"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>Thrust (Sea Level, kN):</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="rocket_engines_thrust_sea_level"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>Thrust (Vacuum, kN):</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="rocket_engines_thrust_vacuum"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>Number:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="rocket_engines_number"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>Type:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="rocket_engines_type"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>Version:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="rocket_engines_version"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>Layout:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="rocket_engines_layout"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>Engine Loss Max:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="rocket_engines_max_loss"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>Propellant 1:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="rocket_engines_propellant1"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>Propellant 2:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="rocket_engines_propellant2"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>Thrust to Weight Ratio:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="rocket_engines_ttwr"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
				<v-col cols="12">
					<b>Landing Legs:</b>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>Number:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="rocket_landing_legs_number"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>Material:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="rocket_landing_legs_material"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
				<v-col cols="12">
					<b>Payload:</b>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>LEO:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="rocket_payload_leo"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>GTO:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="rocket_payload_gto"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>Mars:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="rocket_payload_mars"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>Pluto:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="rocket_payload_pluto"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="top">
    		<v-col cols="3">
					<b>Description:</b>
				</v-col>
				<v-col cols="9">
					<v-textarea
						:value="rocket_description"
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
					<a :href="rocket_wikipedia" target="_blank" v-if="rocket_wikipedia !== ''">
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
	name: 'LaunchpadMap',
	components: {
		
	},
	data() {
		return {
			rocket_id: '',
			rocket_name: '',
			rocket_type: '',
			rocket_active: '',
			rocket_photo: require('@/assets/image_placeholder.png'),
			photoWidth: 0,
			rocket_company: '',
			rocket_country: '',
			rocket_first_flight: '',
			rocket_sr: '',
			rocket_cost: '',
			rocket_stages: '',
			rocket_boosters: '',
			rocket_height: '',
			rocket_diameter: '',
			rocket_mass: '',
			rocket_first_stage_thrust_sea_level: '',
			rocket_first_stage_thrust_vacuum: '',
			rocket_first_stage_reusable: '',
			rocket_first_stage_engines: '',
			rocket_first_stage_fuel_amount: '',
			rocket_first_stage_burn_time: '',
			rocket_second_stage_thrust: '',
			rocket_second_stage_payloads: [],
			rocket_second_stage_reusable: '',
			rocket_second_stage_engines: '',
			rocket_second_stage_fuel_amount: '',
			rocket_second_stage_burn_time: '',
			rocket_engines_isp_sea_level: '',
			rocket_engines_isp_vacuum: '',
			rocket_engines_thrust_sea_level: '',
			rocket_engines_thrust_vacuum: '',
			rocket_engines_number: '',
			rocket_engines_type: '',
			rocket_engines_version: '',
			rocket_engines_layout: '',
			rocket_engines_max_loss: '',
			rocket_engines_propellant1: '',
			rocket_engines_propellant2: '',
			rocket_engines_ttwr: '',
			rocket_landing_legs_number: '',
			rocket_landing_legs_material: '',
			rocket_payload_leo: '',
			rocket_payload_gto: '',
			rocket_payload_mars: '',
			rocket_payload_pluto: '',
			rocket_description: '',
			rocket_wikipedia: '',
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
			if(that.$route.params.type === 'rocket') {
				that.rocket_id = that.$route.params.id
				that.loadRocket()
			}
		} else if(Object.keys(that.$route.query).length > 0){
			if(that.$route.query.type === 'rocket') {
				that.rocket_id = that.$route.query.id
				that.loadRocket()
			}
		}
	},
	methods: {
		resizeHandler(){
			this.photoWidth = (document.getElementById('detailMain').getBoundingClientRect().width)*0.25-31.875
    },
    loadRocket() {
			var that = this
			axios.get('https://api.spacexdata.com/v4/rockets/'+this.rocket_id)
      .then(function (response) {
				that.rocket_name = response.data.name
				that.rocket_type = response.data.type
				that.rocket_active = response.data.active
				that.rocket_photo = response.data.flickr_images[0]
				that.rocket_company = response.data.company
				that.rocket_country = response.data.country
				that.rocket_first_flight = response.data.first_flight
				that.rocket_sr = response.data.success_rate_pct
				that.rocket_cost = response.data.cost_per_launch
				that.rocket_stages = response.data.stages
				that.rocket_boosters = response.data.boosters
				that.rocket_height = response.data.height.meters
				that.rocket_diameter = response.data.diameter.meters
				that.rocket_mass = response.data.mass.kg
				that.rocket_first_stage_thrust_sea_level = response.data.first_stage.thrust_sea_level.kN
				that.rocket_first_stage_thrust_vacuum = response.data.first_stage.thrust_vacuum.kN
				that.rocket_first_stage_reusable = response.data.first_stage.reusable
				that.rocket_first_stage_engines = response.data.first_stage.engines
				that.rocket_first_stage_fuel_amount = response.data.first_stage.fuel_amount_tons
				that.rocket_first_stage_burn_time = response.data.first_stage.burn_time_sec
				that.rocket_second_stage_thrust = response.data.second_stage.thrust.kN
				that.rocket_second_stage_payloads = JSON.stringify(response.data.second_stage.payloads, null, 2)
				that.rocket_second_stage_reusable = response.data.second_stage.reusable
				that.rocket_second_stage_engines = response.data.second_stage.engines
				that.rocket_second_stage_fuel_amount = response.data.second_stage.fuel_amount_tons
				that.rocket_second_stage_burn_time = response.data.second_stage.burn_time_sec
				that.rocket_engines_isp_sea_level = response.data.engines.isp.sea_level
				that.rocket_engines_isp_vacuum = response.data.engines.isp.vacuum
				that.rocket_engines_thrust_sea_level = response.data.engines.thrust_sea_level.kN
				that.rocket_engines_thrust_vacuum = response.data.engines.thrust_vacuum.kN
				that.rocket_engines_number = response.data.engines.number
				that.rocket_engines_type = response.data.engines.type
				that.rocket_engines_version = response.data.engines.version
				that.rocket_engines_layout = response.data.engines.layout
				that.rocket_engines_max_loss = response.data.engines.engine_loss_max
				that.rocket_engines_propellant1 = response.data.engines.propellant_1
				that.rocket_engines_propellant2 = response.data.engines.propellant_2
				that.rocket_engines_ttwr = response.data.engines.thrust_to_weight
				that.rocket_landing_legs_number = response.data.landing_legs.number
				that.rocket_landing_legs_material = response.data.landing_legs.material
				if(response.data.payload_weights.length === 1) {
						that.rocket_payload_leo = response.data.payload_weights[0].kg
				} else if(response.data.payload_weights.length === 2) {
					that.rocket_payload_leo = response.data.payload_weights[0].kg
					that.rocket_payload_gto = response.data.payload_weights[1].kg
				} else if(response.data.payload_weights.length === 3) {
					that.rocket_payload_leo = response.data.payload_weights[0].kg
					that.rocket_payload_gto = response.data.payload_weights[1].kg
					that.rocket_payload_mars = response.data.payload_weights[2].kg
				} else if(response.data.payload_weights.length === 4) {
					that.rocket_payload_leo = response.data.payload_weights[0].kg
					that.rocket_payload_gto = response.data.payload_weights[1].kg
					that.rocket_payload_mars = response.data.payload_weights[2].kg
					that.rocket_payload_pluto = response.data.payload_weights[3].kg
				}
				that.rocket_description = response.data.description
				that.rocket_wikipedia = response.data.wikipedia
      })
      .catch(function (error) {
        console.log(error);
      })
		}
	},
}
</script>