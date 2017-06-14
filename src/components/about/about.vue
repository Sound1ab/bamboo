<script type="text/babel">
	import {firstWord} from '../helpers/regex';

	export default {
		name: 'about',
		props: ['data'],
		data () {
			return {
				id: 29,
				postData: [],
			};
		},
		beforeMount () {
			let refinedData = this.data.filter(post => {
				return post.id === this.id;
			});
			this.postData = refinedData[0].acf;
			console.group('postData');
			console.log('this.postData', this.postData);
			console.groupEnd('postData');
		},
		computed: {
			renderPosts () {
				for (let prop in this.postData) {
					if (this.postData.hasOwnProperty(prop)) {
						let digit = prop.match(/'\d+'/);
						let string = prop.match(firstWord);
//					if (this.postData[prop])
						console.group('log');
						console.log('digit', digit);
						console.log('string', string);
						console.groupEnd('log');
					}
				}
			},
		},
		render (h) {
			return (
				<div>
					{this.renderPosts()}
				</div>
			);
		},
	};
</script>

<style lang="scss" type="text/scss">

</style>
