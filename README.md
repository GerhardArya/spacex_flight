# SpaceX Insight

A simple web application that provides some insight and visualization of the data provided by [r/SpaceX API V4 Docs](https://github.com/r-spacex/SpaceX-API/tree/master/docs/v4).

## Disclaimer
Neither this web application nor the API are affiliated, associated, authorized, endorsed by, or in any way officially connected with Space Exploration Technologies Inc (SpaceX), or any of its subsidiaries or its affiliates. The names SpaceX as well as related names, marks, emblems and images are registered trademarks of their respective owners.

## Features
* Company information of SpaceX
* A timeline of SpaceX's historical events
* Dashboard with charts and graphs to visualize data
* Tabularized overview of data provided by every endpoint of the API (non auth ones)
* Detailed view of a particular entry with a seperate component for each entry type
* Links to other relevant entries for easier navigation

## Local Usage
Using console:
1. Clone this repository
2. Go to the project's root directory
3. ```npm install```
4. ```npm run dev```

## Hosted Demo
[Web-App hosted on Firebase](https://spacex-insight.web.app/)

## Made with
* [Nuxt.JS](https://github.com/nuxt/nuxt.js)
* [Vuetify](https://github.com/vuetifyjs/vuetify)
* [Axios](https://github.com/axios/axios)
* [Vue-ApexCharts](https://github.com/apexcharts/vue-apexcharts)

## Future Development
* More charts and graphs for the dashboard
* User interaction with the charts and graphs
* Implement the query function for the tabularized overview

## Note
* The Fairings endpoint of the API seems to provide nothing, this is not an error of the web application
* Two svg map chart components exist in the project directory. This is an unfinished component for the dashboard, feature cut due to time constraints.
