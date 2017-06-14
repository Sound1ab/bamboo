<script>
	import NavBar from './components/header/navbar.vue';
	import Header from './components/header/header';
	import About from './components/about/about';
	import fetch from 'isomorphic-fetch';

	export default {
		name: 'app',
		components: {
			NavBar,
			Header,
			About,
		},
		data () {
			return {
				apiResponse: [],
			};
		},
		beforeCreate () {
			fetch('//phillipparker.tech/wp-json/acf/v3/posts/')
				.then(response => {
					if (response.status >= 400) {
						throw new Error('Bad response from server');
					}
					return response.json();
				})
				.then(response => {
					this.apiResponse = response;
				});
		},
		render (h) {
			return (
				<div class="app">
					{this.apiResponse.length > 0
						? <div>
							<NavBar data={this.apiResponse}/>
							<Header data={this.apiResponse}/>
							<About data={this.apiResponse}/>
						</div> : null
					}
				</div>
			);
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
