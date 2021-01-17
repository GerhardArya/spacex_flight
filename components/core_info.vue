<template>
  <v-row justify="center" align="center">
    <v-col cols="12">
      <v-row justify="start" align="center">
    		<v-col cols="3">
					<b>ID:</b>
				</v-col>
				<v-col cols="7">
					<v-text-field
            v-model="core_id"
            solo
						hide-details
          ></v-text-field>
				</v-col>
				<v-col cols="2">
					<v-btn @click="loadCore">Search</v-btn>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Serial:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="core_serial"
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
            :value="core_status"
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
					<v-row v-for="item in core_launches" class="px-3 py-2">
						<a :href="item.link">{{ item.id }}</a>
					</v-row>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Block:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="core_block"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>RTLS Attempt:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="core_rtls_attempts"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>RTLS Landings:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="core_rtls_landings"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>ASDS Attempt:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="core_asds_attempts"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>ASDS Landings:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="core_asds_landings"
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
            :value="core_reuse"
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
						:value="core_last_update"
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
	name: 'CoreInfo',
	components: {
		
	},
	data() {
		return {
			core_id: '',
			core_serial: '',
			core_status: '',
			core_launches: [],
			core_block: '',
			core_rtls_attempts: '',
			core_rtls_landings: '',
			core_asds_attempts: '',
			core_asds_landings: '',
			core_reuse: '',
			core_last_update: '',
		}
	},
	mounted(){
		var that = this
		if(Object.keys(that.$route.params).length > 0){
			if(that.$route.params.type === 'core') {
				that.core_id = that.$route.params.id
				that.loadCore()
			}
		} else if(Object.keys(that.$route.query).length > 0){
			if(that.$route.query.type === 'core') {
				that.core_id = that.$route.query.id
				that.loadCore()
			}
		}
	},
	methods: {
    loadCore() {
			var that = this
			axios.get('https://api.spacexdata.com/v4/cores/'+this.core_id)
      .then(function (response) {
				that.core_serial = response.data.serial
				that.core_status = response.data.status
				response.data.launches.forEach(launchID => {
					that.core_launches.push({
						id: launchID,
						link: "/details?id="+launchID+"&type=launch"
					})
				});
				that.core_block = response.data.block
				that.core_rtls_attempts = response.data.rtls_attempts
				that.core_rtls_landings = response.data.rtls_landings
				that.core_asds_attempts = response.data.asds_attempts
				that.core_asds_landings = response.data.asds_attempts
				that.core_reuse = response.data.reuse_count
				that.core_last_update = response.data.last_update
      })
      .catch(function (error) {
        console.log(error);
      })
		}
	},
}
</script>