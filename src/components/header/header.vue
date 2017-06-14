<script type="text/babel">
	export default {
		name: 'header',
		props: ['data'],
		data () {
			return {
				id: 10,
				postData: [],
			};
		},
		beforeMount () {
			let refinedData = this.data.filter(post => {
				return post.id === this.id;
			});
			this.postData = refinedData[0].acf;
		},
		render (h) {
			return (
				<div class="header">
					<div class="header__container">
						<img class="header__logo" src={this.postData.logo}/>
					</div>
					<h1 class="header__floating-title">{this.postData.floating_title}</h1>
				</div>
			);
		},
	};
</script>

<style lang="scss" type="text/scss">
	@import "~styles/main.scss";

	.header {
		padding: em(100, $fzBase) 0 0 0;
		background-color: white;

		&__container {
			display: flex;
			flex-direction: row;
			justify-content: center;
		}

		&__logo {
			width: 189px;
			height: auto;
		}

		&__floating-title {
			font-size: em(105, $fzBase);
			font-weight: bold;
			color: black;
		}
	}
</style>
