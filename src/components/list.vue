<template>
	<div class="list">
		<ul>
			<li v-for="name in li">{{name}}</li>
		</ul>

		<input type="text" v-model="inputValue"/>
		<button @click="handleClick">add name</button>
	</div>
</template>

<script>
	export default {
		name: 'list',
		data () {
			return {
				li: ['a', 'e', 'c'],
				inputValue: ''
			}
		},
		methods: {
			handleClick () {
				this.li = [...this.li, this.inputValue]
			}
		}
	}
</script>
