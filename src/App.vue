<template>
	<div id="app">
		<header class="header">
			<nav class="container navbar">
				<div class="navbar-brand">
					<img alt="Logo" src="./assets/logo.png">
				</div>
			</nav>
		</header>

		<section>
			<p>users.gender</p>
		</section>

		<router-view></router-view>

		<footer class="footer">
			<div class="content has-text-centered">
				<p>&copy; 2019 Shannon Frederick</p>
			</div>
		</footer>
	</div>
</template>

<script>
import axios from "axios"

export default {
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

<style>
#app {
	font-family: 'Quicksand', sans-serif;
}

.header {
	border-bottom: 1px solid #eee;
}

.footer {
	background-color: #eee;
}
</style>
