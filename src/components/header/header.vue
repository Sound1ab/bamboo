<template>
	<div class="header">
		<NavBar></NavBar>
		<div class="big-logo">
			<div>
				<img src="../../assets/images/logo.png" />
			</div>
			<h1>BAM • BOO</h1>
		</div>
	</div>
</template>

<script>
	import NavBar from './navbar.vue'

	export default {
		name: 'header',
		components: {
			NavBar,
		},
		data () {
			return {
				someData: '',
			}
		},
//		methods: {
//
//		}
	}
</script>

<style lang="scss" rel="text/scss">
	.header {
		position: relative;
		height: 550px;
		background-color: aliceblue;

		.big-logo {
			position: absolute;
			top: 0;
			left: 0;
			width: 100%;
			height: 100%;
			display: flex;
			flex-direction: column;
			justify-content: center;

			h1 {
				font-size: 105px;
				font-weight: bold;
				margin-top: 25px;
				color: white;
			}
		}
	}
</style>
