<template>
	<section class="section">
		<div class="container">
			<a v-on:click="downloadCSV" class="button is-light">
				Export to CSV
			</a>

			<div class="tile is-parent" v-for="user in users" :key="user.id.value" >
				<img :alt="`${user.name.first} ${user.name.last} Image`"
				:src="user.picture.large"/>

				<article class="user-info is-verticle">
					<p class="capitalize"><strong>{{ user.name.first }} {{ user.name.last }}</strong></p>
					<p class="capitalize">Age: {{ user.dob.age }}</p>
					<p class="capitalize">Gender: {{ user.gender }}</p>
					<p>Email: {{ user.email }}</p>
					<p>Phone: {{ user.phone }}</p>
				</article>
			</div>

			<nav class="is-centered" role="navigation" aria-label="pagination">
				<a v-on:click="getPrevPage" class="button is-light">Previous</a>
				<a v-on:click="getNextPage" class="button is-light">Next page</a>
			</nav>
		</div>
	</section>
</template>

<script>
import axios from "axios"

export default {
	name: 'Results',
	data() {
		return {
			users: [],
			page: 1
		}
	},
	methods: {
		async getUsers() {
			const { data: { results } } = await axios.get(`https://randomuser.me/api/?page=${this.page}&results=10&seed=random`)

			this.users = results;
		},
		async downloadCSV() {
			const { data } = await axios.get(`https://randomuser.me/api/?page=${this.page}&results=10&seed=random&exc=login,nat,cell,registered,location&format=csv&dl`);

			console.log(data); // eslint-disable-line
		},
		async getNextPage() {
			this.page += 1;

			if (this.page == 0) this.page = 1;

			await this.getUsers();
		},
		async getPrevPage() {
			this.page -= 1;

			if (this.page == 0) this.page = 1;

			await this.getUsers();
		},
	},
	async created() {
		await this.getUsers();
	}
}
</script>

<style scoped>
.user-info {
	padding-left: 1rem;
}
</style>
