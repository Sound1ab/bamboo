<script type="text/babel">
	import NavBar from './navbar.vue'

	export default {
		name: 'header',
		components: {
			NavBar,
		},
		props: ['data'],
		data () {
			return {
				id: 10,
				postData: [],
			}
		},
		beforeMount () {
			console.log('this.data', this.data)
			let refinedData = this.data.filter(post => {
				return post.id === this.id
			})
			console.log('refinedData', refinedData)
			this.postData = refinedData[0].acf
		},
//		methods: {
//
//		},
		render (h) {
			return (
				<div class="header">
					<NavBar />
					<div class="big-logo">
						<div>
							<img src={this.postData.pic}/>
						</div>
						<h1>BAM • BOO</h1>
					</div>
				</div>
			)
		},
	}
</script>

<style lang="scss" rel="text/scss">
	.header {
		position: relative;
		height: 550px;
		background-color: aliceblue;
	}

	.big-logo {
		position: absolute;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		display: flex;
		flex-direction: column;
		justify-content: center;
	}

	h1 {
		font-size: 105px;
		font-weight: bold;
		margin-top: 25px;
		color: white;
	}
</style>
