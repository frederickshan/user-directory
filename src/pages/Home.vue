<template>
	<section class="section">
		<div class="container">
			<div class="rows has-text-centered">
				<article class="row is-full introduction">
					<p><strong>Welcome to Dir</strong>, a directory of users.</p>
					<p>Click the button below to view our user results.</p>
				</article>

				<div class="row is-full">
					<router-link class="capitalize button is-light" to="/results">
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
