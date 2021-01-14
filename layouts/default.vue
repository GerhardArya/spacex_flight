<template>
  <v-app>
    <v-navigation-drawer
      v-model="drawer"
      mini-variant
      fixed
      app
    >
      <v-list>
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action>
            <v-tooltip right>
              <template v-slot:activator="{ on, attrs }">
                <v-icon
                  v-bind="attrs"
                  v-on="on"
                >
                  {{ item.icon }}
                </v-icon>
              </template>
              <span>{{ item.title }}</span>
            </v-tooltip>
          </v-list-item-action>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar
      fixed
      app
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-toolbar-title v-text="title" />
    </v-app-bar>
    <v-main>
      <v-container>
        <nuxt />
      </v-container>
    </v-main>
  </v-app>
</template>

<script>
export default {
  data () {
    return {
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'mdi-home',
          title: 'Home',
          to: '/'
        },
        {
          icon: 'mdi-history',
          title: 'Historical Events',
          to: '/historical_events'
        },
        {
          icon: 'mdi-apps',
          title: 'Dashboard',
          to: '/dashboard'
        },
        {
          icon: 'mdi-table-large',
          title: 'Data Overview',
          to: '/data_overview'
        }
      ],
      title: 'SpaceX Insight'
    }
  }
}
</script>
