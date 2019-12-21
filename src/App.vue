<template>
	<div id="app">
		<header class="header">
			<nav class="container navbar">
				<div class="navbar-brand">
					<img alt="Logo" src="./assets/logo.png">
				</div>
			</nav>
		</header>

		<router-view></router-view>

		<footer class="footer">
			<div class="content has-text-centered">
				<p>&copy; 2019 Shannon Frederick</p>
			</div>
		</footer>
	</div>
</template>

<style lang="scss">
#app {
	font-family: 'Quicksand', sans-serif;
}

.button {
	font-weight: 700;
}

.header {
	border-bottom: 1px solid #eee;
}

.footer {
	background-color: #eee;
}
</style>
