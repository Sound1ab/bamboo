<template>
	<div class="about">
		<div class="about__copy-wrap" v-for="prop in postData">
			<h2 class="about__heading beta">{{prop.title}}</h2>
			<p class="about__paragraph">{{prop.copy}}</p>
		</div>
	</div>
</template>

<script type="text/babel">
//	import {firstWord} from '../helpers/regex';

	export default {
		name: 'about',
		props: ['data'],
		data () {
			return {
				id: 92,
				postData: {},
			};
		},
		beforeMount () {
			let refinedData = this.data.filter(post => {
				return post.id === this.id;
			});
			this.postData = refinedData[0].acf.attributes;
		},
	};
</script>

<style lang="scss" type="text/scss">
	@import "~styles/main.scss";

	.about {
		padding-top: em(50);
		display: flex;
		flex-direction: column;
		align-items: center;

		&__copy-wrap {
			max-width: em(800);
		}

		&__heading {
			margin-bottom: em(25);
		}

		&__paragraph {
			margin-bottom: em(40);
		}
	}
</style>
