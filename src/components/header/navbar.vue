<template>
	<nav class="navigation">
		<div class="navigation__logo">
			bam boo
		</div>
		<ul class="navigation__menu">
			<li class="navigation__menu-items" v-for="prop in menuData">{{prop}}</li>
		</ul>
	</nav>
</template>

<script type="text/babel">
	export default {
		name: 'header',
		props: ['data'],
		data () {
			return {
				id: 10,
				menuData: [],
			};
		},
		created () {
			this.data.forEach(post => {
				if (post.acf.navigation_item) {
					this.menuData = [...this.menuData, post.acf.navigation_item];
				}
			});
		},
	};
</script>

<style lang="scss" type="text/scss">
	@import "~styles/main.scss";

	.navigation {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		display: flex;
		flex-direction: row;
		justify-content: space-between;
		height: em(90, $fzBase);
		align-items: center;
		background-color: white;

		&__logo {
			flex-grow: 1;
			display: flex;
			flex-direction: row;
			justify-content: flex-start;
			margin-left: em(80, $fzBase);
		}

		&__menu {
			flex-grow: 1;
			display: flex;
			flex-direction: row;
			justify-content: flex-end;
			margin-right: em(80, $fzBase);
		}

		&__menu-items {
			padding-right: em(10, $fzBase);
			cursor: pointer;
			transition: all 1s ease-in-out;

			&:hover {
				color: #ffff99;
			}

			&:last-child {
				padding-right: 0;
			}
		}
	}
</style>
