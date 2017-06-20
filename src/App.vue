<template>
	<div class="app">
		<span v-if="dataReady">
			<div v-for="element in elements" :is="element.type" :data="apiResponse"></div>
		</span>
	</div>
</template>

<script>
	import navBar from './components/header/navbar.vue';
	import hero from './components/header/hero';
	import about from './components/about/about';
	import location from './components/locations/locations';
	import fetch from 'isomorphic-fetch';

	export default {
		name: 'app',
		components: {
			navBar,
			hero,
			about,
			location,
		},
		methods: {
			fetchData () {
				fetch('//phillipparker.tech/wp-json/acf/v3/posts/')
					.then(response => {
						if (response.status >= 400) {
							throw new Error('Bad response from server');
						}
						return response.json();
					})
					.then(response => {
						this.apiResponse = response;
						console.group('data');
						console.log('response', response);
						console.groupEnd('data');
						this.dataReady = true;
					});
			},
		},
		data () {
			return {
				apiResponse: [],
				dataReady: false,
				elements: [
					{type: 'nav-bar'},
					{type: 'hero'},
					{type: 'about'},
					{type: 'location'},
				],
			};
		},
		created () {
			this.fetchData();
		},
	};
</script>

<style lang="scss">
	@import "~styles/main.scss";

	.app {
		position: relative;
		font-family: $ffBase;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
		text-align: center;
		color: #2c3e50;
		max-width: 1200px;
		margin: 0 auto;
	}
</style>
