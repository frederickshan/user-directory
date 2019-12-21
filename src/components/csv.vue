<template>
	<div class="columns">
		<button v-on:click="downloadCSV" class="button is-light is-size-6">
			Export to CSV
		</button>
	</div>
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
	computed: {
		isDisabled() {
			return this.page == 1;
		}
	},
	methods: {
		async getUsers() {
			const { data: { results } } = await axios.get(`https://randomuser.me/api/?page=${this.page}&results=10&seed=random`)

			this.users = results;
		},
		async downloadCSV() {
			const { data } = await axios.get(`https://randomuser.me/api/?page=${this.page}&results=10&seed=random&exc=login,nat,cell,registered,location&format=csv&dl`);

			const a = document.createElement("a");
			a.style.display = "none";
			document.body.appendChild(a);

			a.href = window.URL.createObjectURL(
				new Blob([data], { type: "text/plain;charset=utf-8" })
			);

			a.setAttribute("download", "users.txt");

			a.click();

			window.URL.revokeObjectURL(a.href);
			document.body.removeChild(a);

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
</style>
