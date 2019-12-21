<template>
	<div class="columns is-centered has-text-centered">
		<nav class="is-centered" role="navigation" aria-label="pagination">
			<button v-on:click="prevPage" class="button is-light is-size-6" :disabled="isDisabled">Previous</button>
			<button v-on:click="nextPage" class="button is-light is-size-6">Next page</button>
		</nav>
	</div>
</template>

<script>
export default {
	Name: 'Pagination',
	props: {
		page: {
			type: Number,
			required: true
		}
	},
	computed: {
		isDisabled() {
			return this.page == 1;
		}
	},
	methods: {
		nextPage() {
			this.$emit('nextPage');
		},
		prevPage() {
			this.$emit('prevPage');
		}
	}
}
</script>
