<template>
  <article class="examples__block">
    <div class="examples__block__map examples__block__map--usa">
      <svg-map
        :map="USA"
        :location-class="getLocationClass"
        @mouseover="pointLocation"
        @mouseout="unpointLocation"
        @mousemove="moveOnLocation"
      />
      <div
        class="examples__block__map__tooltip"
        :style="tooltipStyle"
      >
        {{ pointedLocation }}
      </div>
    </div>
  </article>
</template>

<script>
import USA from '@svg-maps/usa'
import { SvgMap } from "vue-svg-map";
export default {
	name: 'LaunchpadMap',
	components: {
		SvgMap,
	},
	data() {
		return {
			USA,
			pointedLocation: null,
			tooltipStyle: null,
		}
	},
	methods: {
    getLocationName(node) {
	    return node && node.attributes.name.value
    },
		pointLocation(event) {
			this.pointedLocation = this.getLocationName(event.target)
		},
		unpointLocation(event) {
			this.pointedLocation = null
			this.tooltipStyle = { display: 'none' }
		},
		moveOnLocation(event) {
			this.tooltipStyle = {
				display: 'block',
				top: `${event.clientY + 10}px`,
				left: `${event.clientX - 100}px`,
			}
		},
		getLocationClass(location, index) {
			// Generate heat map
			return `svg-map__location svg-map__location--heat${index % 4}`
		},
	},
}
</script>
<style lang="scss">
.examples {
	width: 1000px;
	margin: 0 auto;
	font-family: Arial, sans-serif;
	text-align: center;

	&__block {
		margin-bottom: 80px;
		padding-bottom: 80px;
		border-bottom: 1px dotted black;

		&__map {
			display: inline-block;
			width: 500px;

			&--usa {
				width: 800px; // USA needs more space	for tooltip

				.svg-map__location {
					&--heat0 {
						fill: blue;
					}

					&--heat1 {
						fill: lightblue;
					}

					&--heat2 {
						fill: orange;
					}

					&--heat3 {
						fill: red;
					}

					&:focus,
					&:hover {
						opacity: 0.75;
					}
				}
			}

			&__tooltip {
				position: fixed;
				width: 200px;
				padding: 10px;
				border: 1px solid darkgray;
				background-color: white;
			}
		}
	}
}
</style>