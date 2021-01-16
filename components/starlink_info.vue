<template>
  <v-row justify="center" align="center">
    <v-col cols="12">
      <v-row justify="start" align="center">
    		<v-col cols="3">
					<b>ID:</b>
				</v-col>
				<v-col cols="7">
					<v-text-field
            v-model="starlink_id"
            solo
						hide-details
          ></v-text-field>
				</v-col>
				<v-col cols="2">
					<v-btn @click="loadStarlink">Search</v-btn>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Version:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="starlink_version"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Launch:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="starlink_launch"
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
            :value="starlink_latitude"
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
            :value="starlink_longitude"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Height (km):</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="starlink_height"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					<b>Velocity (km/s)</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="starlink_velocity"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
				<v-col cols="12">
					<b>Space Track:</b>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>CCSDS_OMM_VERS:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="starlink_CCSDS_OMM_VERS"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>COMMENT:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="starlink_COMMENT"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>CREATION_DATE:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="starlink_CREATION_DATE"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>ORIGINATOR:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="starlink_ORIGINATOR"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>OBJECT_NAME:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="starlink_OBJECT_NAME"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>OBJECT_ID:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="starlink_OBJECT_ID"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>CENTER_NAME:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="starlink_CENTER_NAME"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>REF_FRAME:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="starlink_REF_FRAME"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>TIME_SYSTEM:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="starlink_TIME_SYSTEM"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>MEAN_ELEMENT_THEORY:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="starlink_MEAN_ELEMENT_THEORY"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>EPOCH:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="starlink_EPOCH"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>MEAN_MOTION:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="starlink_MEAN_MOTION"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>ECCENTRICITY:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="starlink_ECCENTRICITY"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>INCLINATION:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
           	:value="starlink_INCLINATION"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>RA_OF_ASC_NODE:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="starlink_RA_OF_ASC_NODE"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>ARG_OF_PERICENTER:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="starlink_ARG_OF_PERICENTER"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>MEAN_ANOMALY:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="starlink_MEAN_ANOMALY"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>EPHEMERIS_TYPE:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="starlink_EPHEMERIS_TYPE"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>CLASSIFICATION_TYPE:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="starlink_CLASSIFICATION_TYPE"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>NORAD_CAT_ID:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="starlink_NORAD_CAT_ID"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>ELEMENT_SET_NO:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="starlink_ELEMENT_SET_NO"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>REV_AT_EPOCH:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="starlink_REV_AT_EPOCH"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>BSTAR:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="starlink_BSTAR"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>MEAN_MOTION_DOT:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="starlink_MEAN_MOTION_DOT"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>MEAN_MOTION_DDOT:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="starlink_MEAN_MOTION_DDOT"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>SEMIMAJOR_AXIS:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="starlink_SEMIMAJOR_AXIS"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>PERIOD:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="starlink_PERIOD"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>APOAPSIS:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="starlink_APOAPSIS"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>PERIAPSIS:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="starlink_PERIAPSIS"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>OBJECT_TYPE:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="starlink_OBJECT_TYPE"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>RCS_SIZE:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="starlink_RCS_SIZE"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>COUNTRY_CODE:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="starlink_COUNTRY_CODE"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>LAUNCH_DATE:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="starlink_LAUNCH_DATE"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>SITE:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="starlink_SITE"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>DECAY_DATE:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="starlink_DECAY_DATE"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>DECAYED:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="starlink_DECAYED"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>FILE:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="starlink_FILE"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>GP_ID:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="starlink_GP_ID"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>TLE_LINE0:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="starlink_TLE_LINE0"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>TLE_LINE1:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="starlink_TLE_LINE1"
            solo
            readonly
						hide-details
          ></v-text-field>
				</v-col>
			</v-row>
			<v-row justify="start" align="center">
    		<v-col cols="3">
					&emsp;
					<b>TLE_LINE2:</b>
				</v-col>
				<v-col cols="9">
					<v-text-field
            :value="starlink_TLE_LINE2"
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
			starlink_id: '',
			starlink_version: '',
			starlink_launch: '',
			starlink_latitude: '',
			starlink_longitude: '',
			starlink_height: '',
			starlink_velocity: '',
			starlink_CCSDS_OMM_VERS: '',
			starlink_COMMENT: '',
			starlink_CREATION_DATE: '',
			starlink_ORIGINATOR: '',
			starlink_OBJECT_NAME: '',
			starlink_OBJECT_ID: '',
			starlink_CENTER_NAME: '',
			starlink_REF_FRAME: '',
			starlink_TIME_SYSTEM: '',
			starlink_MEAN_ELEMENT_THEORY: '',
			starlink_EPOCH: '',
			starlink_MEAN_MOTION: '',
			starlink_ECCENTRICITY: '',
			starlink_INCLINATION: '',
			starlink_RA_OF_ASC_NODE: '',
			starlink_ARG_OF_PERICENTER: '',
			starlink_MEAN_ANOMALY: '',
			starlink_EPHEMERIS_TYPE: '',
			starlink_CLASSIFICATION_TYPE: '',
			starlink_NORAD_CAT_ID: '',
			starlink_ELEMENT_SET_NO: '',
			starlink_REV_AT_EPOCH: '',
			starlink_BSTAR: '',
			starlink_MEAN_MOTION_DOT: '',
			starlink_MEAN_MOTION_DDOT: '',
			starlink_SEMIMAJOR_AXIS: '',
			starlink_PERIOD: '',
			starlink_APOAPSIS: '',
			starlink_PERIAPSIS: '',
			starlink_OBJECT_TYPE: '',
			starlink_RCS_SIZE: '',
			starlink_COUNTRY_CODE: '',
			starlink_LAUNCH_DATE: '',
			starlink_SITE: '',
			starlink_DECAY_DATE: '',
			starlink_DECAYED: '',
			starlink_FILE: '',
			starlink_GP_ID: '',
			starlink_TLE_LINE0: '',
			starlink_TLE_LINE1: '',
			starlink_TLE_LINE2: ''
		}
	},
	mounted(){
		var that = this
		if(Object.keys(this.$route.params).length > 0){
			if(this.$route.params.type === 'starlink') {
				axios.get('https://api.spacexdata.com/v4/starlink/'+this.$route.params.id)
      	.then(function (response) {
					that.starlink_id = response.data.id
					that.starlink_version = response.data.version
					that.starlink_launch = response.data.launch
					that.starlink_latitude = response.data.latitude
					that.starlink_longitude = response.data.longitude
					that.starlink_height = response.data.height_km
					that.starlink_velocity = response.data.velocity_kms
					that.starlink_CCSDS_OMM_VERS = response.data.spaceTrack.CCSDS_OMM_VERS
					that.starlink_COMMENT = response.data.spaceTrack.COMMENT
					that.starlink_CREATION_DATE = response.data.spaceTrack.CREATION_DATE
					that.starlink_ORIGINATOR = response.data.spaceTrack.ORIGINATOR
					that.starlink_OBJECT_NAME = response.data.spaceTrack.OBJECT_NAME
					that.starlink_OBJECT_ID = response.data.spaceTrack.OBJECT_ID
					that.starlink_CENTER_NAME = response.data.spaceTrack.CENTER_NAME
					that.starlink_REF_FRAME = response.data.spaceTrack.REF_FRAME
					that.starlink_TIME_SYSTEM = response.data.spaceTrack.TIME_SYSTEM
					that.starlink_MEAN_ELEMENT_THEORY = response.data.spaceTrack.MEAN_ELEMENT_THEORY
					that.starlink_EPOCH = response.data.spaceTrack.EPOCH
					that.starlink_MEAN_MOTION = response.data.spaceTrack.MEAN_MOTION
					that.starlink_ECCENTRICITY = response.data.spaceTrack.ECCENTRICITY
					that.starlink_INCLINATION = response.data.spaceTrack.INCLINATION
					that.starlink_RA_OF_ASC_NODE = response.data.spaceTrack.RA_OF_ASC_NODE
					that.starlink_ARG_OF_PERICENTER = response.data.spaceTrack.ARG_OF_PERICENTER
					that.starlink_MEAN_ANOMALY = response.data.spaceTrack.MEAN_ANOMALY
					that.starlink_EPHEMERIS_TYPE = response.data.spaceTrack.EPHEMERIS_TYPE
					that.starlink_CLASSIFICATION_TYPE = response.data.spaceTrack.CLASSIFICATION_TYPE
					that.starlink_NORAD_CAT_ID = response.data.spaceTrack.NORAD_CAT_ID
					that.starlink_ELEMENT_SET_NO = response.data.spaceTrack.ELEMENT_SET_NO
					that.starlink_REV_AT_EPOCH = response.data.spaceTrack.REV_AT_EPOCH
					that.starlink_BSTAR = response.data.spaceTrack.BSTAR
					that.starlink_MEAN_MOTION_DOT = response.data.spaceTrack.MEAN_MOTION_DOT
					that.starlink_MEAN_MOTION_DDOT = response.data.spaceTrack.MEAN_MOTION_DDOT
					that.starlink_SEMIMAJOR_AXIS = response.data.spaceTrack.SEMIMAJOR_AXIS
					that.starlink_PERIOD = response.data.spaceTrack.PERIOD
					that.starlink_APOAPSIS = response.data.spaceTrack.APOAPSIS
					that.starlink_PERIAPSIS = response.data.spaceTrack.PERIAPSIS
					that.starlink_OBJECT_TYPE = response.data.spaceTrack.OBJECT_TYPE
					that.starlink_RCS_SIZE = response.data.spaceTrack.RCS_SIZE
					that.starlink_COUNTRY_CODE = response.data.spaceTrack.COUNTRY_CODE
					that.starlink_LAUNCH_DATE = response.data.spaceTrack.LAUNCH_DATE
					that.starlink_SITE = response.data.spaceTrack.SITE
					that.starlink_DECAY_DATE = response.data.spaceTrack.DECAY_DATE
					that.starlink_DECAYED = response.data.spaceTrack.DECAYED
					that.starlink_FILE = response.data.spaceTrack.FILE
					that.starlink_GP_ID = response.data.spaceTrack.GP_ID
					that.starlink_TLE_LINE0 = response.data.spaceTrack.TLE_LINE0
					that.starlink_TLE_LINE1 = response.data.spaceTrack.TLE_LINE1
					that.starlink_TLE_LINE2 = response.data.spaceTrack.TLE_LINE2
      	})
      	.catch(function (error) {
        	console.log(error);
      	})
			}
		}
	},
	methods: {
    loadStarlink() {
			var that = this
			axios.get('https://api.spacexdata.com/v4/starlink/'+this.starlink_id)
      .then(function (response) {
				that.starlink_version = response.data.version
				that.starlink_launch = response.data.launch
				that.starlink_latitude = response.data.latitude
				that.starlink_longitude = response.data.longitude
				that.starlink_height = response.data.height_km
				that.starlink_velocity = response.data.velocity_kms
				that.starlink_CCSDS_OMM_VERS = response.data.spaceTrack.CCSDS_OMM_VERS
				that.starlink_COMMENT = response.data.spaceTrack.COMMENT
				that.starlink_CREATION_DATE = response.data.spaceTrack.CREATION_DATE
				that.starlink_ORIGINATOR = response.data.spaceTrack.ORIGINATOR
				that.starlink_OBJECT_NAME = response.data.spaceTrack.OBJECT_NAME
				that.starlink_OBJECT_ID = response.data.spaceTrack.OBJECT_ID
				that.starlink_CENTER_NAME = response.data.spaceTrack.CENTER_NAME
				that.starlink_REF_FRAME = response.data.spaceTrack.REF_FRAME
				that.starlink_TIME_SYSTEM = response.data.spaceTrack.TIME_SYSTEM
				that.starlink_MEAN_ELEMENT_THEORY = response.data.spaceTrack.MEAN_ELEMENT_THEORY
				that.starlink_EPOCH = response.data.spaceTrack.EPOCH
				that.starlink_MEAN_MOTION = response.data.spaceTrack.MEAN_MOTION
				that.starlink_ECCENTRICITY = response.data.spaceTrack.ECCENTRICITY
				that.starlink_INCLINATION = response.data.spaceTrack.INCLINATION
				that.starlink_RA_OF_ASC_NODE = response.data.spaceTrack.RA_OF_ASC_NODE
				that.starlink_ARG_OF_PERICENTER = response.data.spaceTrack.ARG_OF_PERICENTER
				that.starlink_MEAN_ANOMALY = response.data.spaceTrack.MEAN_ANOMALY
				that.starlink_EPHEMERIS_TYPE = response.data.spaceTrack.EPHEMERIS_TYPE
				that.starlink_CLASSIFICATION_TYPE = response.data.spaceTrack.CLASSIFICATION_TYPE
				that.starlink_NORAD_CAT_ID = response.data.spaceTrack.NORAD_CAT_ID
				that.starlink_ELEMENT_SET_NO = response.data.spaceTrack.ELEMENT_SET_NO
				that.starlink_REV_AT_EPOCH = response.data.spaceTrack.REV_AT_EPOCH
				that.starlink_BSTAR = response.data.spaceTrack.BSTAR
				that.starlink_MEAN_MOTION_DOT = response.data.spaceTrack.MEAN_MOTION_DOT
				that.starlink_MEAN_MOTION_DDOT = response.data.spaceTrack.MEAN_MOTION_DDOT
				that.starlink_SEMIMAJOR_AXIS = response.data.spaceTrack.SEMIMAJOR_AXIS
				that.starlink_PERIOD = response.data.spaceTrack.PERIOD
				that.starlink_APOAPSIS = response.data.spaceTrack.APOAPSIS
				that.starlink_PERIAPSIS = response.data.spaceTrack.PERIAPSIS
				that.starlink_OBJECT_TYPE = response.data.spaceTrack.OBJECT_TYPE
				that.starlink_RCS_SIZE = response.data.spaceTrack.RCS_SIZE
				that.starlink_COUNTRY_CODE = response.data.spaceTrack.COUNTRY_CODE
				that.starlink_LAUNCH_DATE = response.data.spaceTrack.LAUNCH_DATE
				that.starlink_SITE = response.data.spaceTrack.SITE
				that.starlink_DECAY_DATE = response.data.spaceTrack.DECAY_DATE
				that.starlink_DECAYED = response.data.spaceTrack.DECAYED
				that.starlink_FILE = response.data.spaceTrack.FILE
				that.starlink_GP_ID = response.data.spaceTrack.GP_ID
				that.starlink_TLE_LINE0 = response.data.spaceTrack.TLE_LINE0
				that.starlink_TLE_LINE1 = response.data.spaceTrack.TLE_LINE1
				that.starlink_TLE_LINE2 = response.data.spaceTrack.TLE_LINE2
      })
      .catch(function (error) {
        console.log(error);
      })
		}
	},
}
</script>