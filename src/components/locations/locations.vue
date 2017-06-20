<template>
	<div class="location">
		<gmap-map
			:center="center"
			:zoom="zoom"
			:options="options"
		>
			<gmap-marker
				:key="index"
				v-for="(m, index) in markers"
				:position="m.position"
				:clickable="true"
				:draggable="true"
				@click="center=m.position"
			></gmap-marker>
		</gmap-map>
	</div>
</template>

<script text="text/babel">
	import * as VueGoogleMaps from 'vue2-google-maps';
	import Vue from 'vue';
	import {styles} from './styling';

	Vue.use(VueGoogleMaps, {
		load: {
			key: 'AIzaSyACNOdWceQvr9HGfb3bJc7nLvrUMoTfKlc',
			// libraries: 'places', //// If you need to use place input
		},
	});

	export default {
		props: ['data'],
		data () {
			return {
				id: 53,
				center: {lat: 51.512974, lng: -0.095420},
				zoom: 13,
				markers: [],
				options: {
					disableDefaultUI: false,
					scrollwheel: false,
					styles,
				},
			};
		},
		created () {
			let refinedData = this.data.filter(post => {
				return post.id === this.id;
			});
			this.markers = refinedData[0].acf.page_attributes.map(coords => {
				return {
					position: {lat: parseFloat(coords.location.lat), lng: parseFloat(coords.location.lng)},
				};
			});
		},
	};
</script>

<style lang="scss" type="text/scss">
	@import "~styles/main.scss";

	.location {
		display: flex;
		flex-direction: row;
		justify-content: center;

	}

	.vue-map-container {
		width: 100% !important;
		height: em(600);
	}

</style>
