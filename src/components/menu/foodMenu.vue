<template>
	<div class="menu">
		<table v-for="section in postData">
			<tr>
				<th v-for="columnHeading in section.section_titles[0]">{{columnHeading}}</th>
			</tr>
			<tr v-for="rowDetails in section.section_items">
				<td v-for="detail in rowDetails"></td>
			</tr>
		</table>
	</div>
</template>

<script type="text/babel">
//	import {firstWord} from '../helpers/regex';

	export default {
		name: 'foodMenu',
		props: ['data'],
		data () {
			return {
				id: 56,
				postData: {},
			};
		},
		beforeMount () {
			let refinedData = this.data.filter(post => {
				return post.id === this.id;
			});
			this.postData = refinedData[0].acf.menu_sections;
			console.log('menu', refinedData);
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
