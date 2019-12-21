<template>
	<section class="section">
		<div class="container">
			<ExportUsers :page="page" />

			<UserTile :users="users"/>

			<Pagination
				v-bind:page.sync="page"
				@nextPage="getNextPage"
				@prevPage="getPrevPage"
			/>
		</div>
	</section>
</template>

<script>
import axios from 'axios';
import UserTile from '@/components/UserTile.vue';
import ExportUsers from '@/components/ExportUsers.vue';
import Pagination from '@/components/Pagination.vue';

export default {
	name: 'Results',
	components: {
		ExportUsers,
		Pagination,
		UserTile
	},
	data() {
		return {
			page: 1,
			users: []
		}
	},
	methods: {
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
		async getUsers() {
			const { data: { results } } = await axios.get(`https://randomuser.me/api/?page=${this.page}&results=10&seed=random`);

			this.users = results;
		}
	},
	async created() {
		await this.getUsers();
	}
}
</script>
