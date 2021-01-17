<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <v-card id="detailMain">
        <v-card-title class="headline">
          Detailed Information
        </v-card-title>
        <v-card-text>
          <v-row justify="center" align="center">
            <v-col cols="2">
              <b>Type:</b> 
            </v-col>
            <v-col cols="10">
              <v-radio-group
                v-model="objectType"
                class="type-radio"
                row
                dense
              >
                <v-radio
                  label="Capsule"
                  value="capsule"
                ></v-radio>
                <v-radio
                  label="Core"
                  value="core"
                ></v-radio>
                <v-radio
                  label="Crew"
                  value="crew"
                ></v-radio>
                <v-radio
                  label="Dragon"
                  value="dragon"
                ></v-radio>
                <v-radio
                  label="Launch"
                  value="launch"
                ></v-radio>
                <v-radio
                  label="Launchpad"
                  value="launchpad"
                ></v-radio>
                <v-radio
                  label="Landpad"
                  value="landpad"
                ></v-radio>
                <v-radio
                  label="Payload"
                  value="payload"
                ></v-radio>
                <v-radio
                  label="Fairing"
                  value="fairing"
                ></v-radio>
                <v-radio
                  label="Rocket"
                  value="rocket"
                ></v-radio>
                <v-radio
                  label="Ship"
                  value="ship"
                ></v-radio>
                <v-radio
                  label="Starlink"
                  value="starlink"
                ></v-radio>
              </v-radio-group>
            </v-col>
          </v-row>
          <v-row justify="center" align="center">
            <v-container fluid>
              <capsule-info v-if="objectType === 'capsule'"/>
              <core-info v-if="objectType === 'core'"/>
              <crew-info v-if="objectType === 'crew'"/>
              <dragon-info v-if="objectType === 'dragon'"/>
              <launch-info v-if="objectType === 'launch'"/>
              <launchpad-info v-if="objectType === 'launchpad'"/>
              <landpad-info v-if="objectType === 'landpad'"/>
              <payload-info v-if="objectType === 'payload'"/>
              <fairing-info v-if="objectType === 'fairing'"/>
              <rocket-info v-if="objectType === 'rocket'"/>
              <ship-info v-if="objectType === 'ship'"/>
              <starlink-info v-if="objectType === 'starlink'"/>
            </v-container>
          </v-row>
        </v-card-text>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
const axios = require('axios');
import CapsuleInfo from '~/components/capsule_info.vue'
import CrewInfo from '~/components/crew_info.vue'
import CoreInfo from '~/components/core_info.vue'
import DragonInfo from '~/components/dragon_info.vue'
import LaunchInfo from '~/components/launch_info.vue'
import LaunchpadInfo from '~/components/launchpad_info.vue'
import LandpadInfo from '~/components/landpad_info.vue'
import PayloadInfo from '~/components/payload_info.vue'
import FairingInfo from '~/components/fairing_info.vue'
import RocketInfo from '~/components/rocket_info.vue'
import ShipInfo from '~/components/ship_info.vue'
import StarlinkInfo from '~/components/starlink_info.vue'
export default {
  components: {
    CapsuleInfo,
    CrewInfo,
    CoreInfo,
    DragonInfo,
    LaunchInfo,
    LaunchpadInfo,
    LandpadInfo,
    PayloadInfo,
    FairingInfo,
    RocketInfo,
    ShipInfo,
    StarlinkInfo,
  },
  head() {
    return {
      title: "Detailed Info"
    };
  },
  data () {
    return {
      objectType: 'capsule',
    }
  },
  mounted(){
    var that = this
    if(Object.keys(this.$route.params).length > 0) {
      that.objectType = that.$route.params.type
    } else if(Object.keys(this.$route.query).length > 0) {
      that.objectType = that.$route.query.type
    }
  },
  methods:{
    
  },
}
</script>
<style>
.type-radio .v-radio {
  padding: 0x;
}
  
.type-radio i {
  font-size: 8px;
}
  
.type-radio label {
  padding-left: 0px;
  font-size: 14px;
}
  
.type-radio [class*="__ripple"] {
  left: 0;
}
</style>
