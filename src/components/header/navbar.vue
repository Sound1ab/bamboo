<template>
	<nav>
		<div class="logo">
			bam boo
		</div>
		<ul>
			<li>Home</li>
			<li>Location</li>
			<li>Menu</li>
			<li>Gallery</li>
		</ul>
	</nav>
</template>

<script>
	export default {
		name: 'header',
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
	nav {
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		height: 90px;
		align-items: center;

		.logo {
			flex-grow: 1;
			display: flex;
			flex-direction: row;
			justify-content: flex-start;
			margin-left: 80px;
		}

		ul {
			flex-grow: 1;
			display: flex;
			flex-direction: row;
			justify-content: flex-end;
			margin-right: 80px;

			li {
				padding-right: 10px;

				&:last-child {
					padding-right: 0;
				}
			}
		}
	}
</style>
