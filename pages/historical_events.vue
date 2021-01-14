<template>
  <v-row justify="center" align="center">
    <v-col cols="12" sm="8" md="6">
      <v-card>
        <v-card-title class="headline">
          Important Historical Events
        </v-card-title>
        <v-card-text>
          <p>All of SpaceX's important historical events as a chronological timeline.</p>
        </v-card-text>
        <v-card-text>
          <v-timeline>
            <v-timeline-item
              v-for="(event, i) in events"
              :key="i"
              :color="event.color"
              small
            >
              <template v-slot:opposite>
                <span
                  :class="`headline font-weight-bold ${event.color}--text`"
                  v-text="event.event_date"
                ></span>
              </template>
              <div class="py-4">
                <h2 :class="`headline font-weight-light mb-4 ${event.color}--text`" :style="`color:${event.color};`">
                  <b>{{ event.title }}</b>
                </h2>
                <div>
                  {{ event.details }}
                </div>
                <div v-if="event.link != null">
                  <a target="_blank" :href="`${event.link}`">Read more</a>.
                </div>
              </div>
            </v-timeline-item>
          </v-timeline>
        </v-card-text>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
const axios = require('axios');
export default {
  components: {
    
  },
  data () {
    return {
      events: [
        
      ],
    }
  },
  mounted(){
    this.init()
  },
  methods:{
    init(){
      var that = this
      axios.get('https://api.spacexdata.com/v4/history')
      .then(function (response) {
        response.data.forEach(function(element, index) {
          var object = {
            details: element.details,
            event_date: element.event_date_utc.split('T')[0].split("-").reverse().join("-"),
            id: element.id,
            link: element.links.article,
            title: element.title,
            color: (index%2==0) ? '#005288' : '#a7a9ac'
          }
          that.events.push(object)
        })
      })
      .catch(function (error) {
        console.log(error);
      })
    }
  },
}
</script>
