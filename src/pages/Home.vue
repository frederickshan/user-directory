<template>
	<section class="section">
		<div class="container">
			<div class="rows has-text-centered">
				<article class="introduction row is-full">
					<p><strong>Welcome to Dir</strong>, a directory of users.</p>
					<p>Click the button below to view the user results.</p>
				</article>

				<div class="row is-full">
					<router-link class="capitalize button is-light is-size-6" to="/results">
						View Results
					</router-link>
				</div>
			</div>
		</div>
	</section>
</template>

<script>
export default {
	name: 'Home'
}
</script>

<style scoped>
.introduction {
	padding-bottom: 3rem;
}
</style>
