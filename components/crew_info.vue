<template>
  <v-row justify="center" align="center">
    <v-col cols="12">
      <v-row justify="start" align="center">
    		<v-col cols="3">
					<b>ID:</b>
				</v-col>
				<v-col cols="7">
					<v-text-field
            v-model="crew_id"
            solo
						hide-details
          ></v-text-field>
				</v-col>
				<v-col cols="2">
					<v-btn @click="loadCrew">Search</v-btn>
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
            				:value="crew_name"
            				solo
            				readonly
										hide-details
          				></v-text-field>
								</v-col>
							</v-row>
							<v-row justify="start" align="center">
								<v-col cols="4">
									<b>Agency:</b>
								</v-col>
								<v-col cols="8">
									<v-text-field
            				:value="crew_agency"
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
            				:value="crew_status"
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
  								:src="crew_photo"
								></v-img>
							</v-row>
						</v-col>
					</v-row>
				</v-col>
			</v-row>
			<v-row justify="start" align="top">
    		<v-col cols="3">
					<b>Launches:</b>
				</v-col>
				<v-col cols="9">
					<v-row v-for="item in crew_launches" class="px-3 py-2">
						<a :href="item.link">{{ item.id }}</a>
					</v-row>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Wikipedia:</b>
				</v-col>
				<v-col cols="9" class="px-3 py-2">
					<a :href="crew_wiki" target="_blank" v-if="crew_wiki !== ''">
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
	name: 'CrewInfo',
	components: {
		
	},
	data() {
		return {
			crew_id: '',
			crew_name: '',
			crew_agency: '',
			crew_status: '',
			crew_photo: require('@/assets/placeholder_portrait.jpg'),
			photoWidth: 0,
			crew_launches: [],
			crew_wiki: ''
		}
	},
	created() {
		this.photoWidth = (document.getElementById('detailMain').getBoundingClientRect().width)*0.25-91.875
    window.addEventListener("resize", this.resizeHandler);
  },
  destroyed() {
    window.removeEventListener("resize", this.resizeHandler);
  },
	mounted(){
		var that = this
		if(Object.keys(that.$route.params).length > 0){
			if(that.$route.params.type === 'crew') {
				that.crew_id = that.$route.params.id
				that.loadCrew()
			}
		} else if(Object.keys(that.$route.query).length > 0){
			if(that.$route.query.type === 'crew') {
				that.crew_id = that.$route.query.id
				that.loadCrew()
			}
		}
	},
	methods: {
		resizeHandler(){
			this.photoWidth = (document.getElementById('detailMain').getBoundingClientRect().width)*0.25-91.875
    },
    loadCrew() {
			var that = this
			axios.get('https://api.spacexdata.com/v4/crew/'+this.crew_id)
      .then(function (response) {
				that.crew_name = response.data.name
				that.crew_agency = response.data.agency
				that.crew_status = response.data.status
				that.crew_photo = response.data.image
				response.data.launches.forEach(launchID => {
					that.crew_launches.push({
						id: launchID,
						link: "/details?id="+launchID+"&type=launch"
					})
				});
				that.crew_wiki = response.data.wikipedia
      })
      .catch(function (error) {
        console.log(error);
      })
		}
	},
}
</script>