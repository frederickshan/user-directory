<template>
	<div class="container">
		<div v-for="user in users" v-bind:key="user.id.value" >
			<img v-bind:src="user.picture.large"/>
		</div>
	</div>
</template>

<script>
import axios from "axios"

export default {
	name: 'Results',
	data() {
		return {
			users: []
		}
	},
	async created() {
		const { data: { results } } = await axios.get("https://randomuser.me/api/?results=50")

		this.users = results;

		console.log(results); // eslint-disable-line
	}
}
</script>

<style scoped>

</style>
