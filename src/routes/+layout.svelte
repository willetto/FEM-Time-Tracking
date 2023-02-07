<script>
</script>

<main>
	<slot />
</main>
<footer class="attribution">
	Challenge by
	<a href="https://www.frontendmentor.io?ref=challenge" target="_blank"> Frontend Mentor</a>. Coded
	by
	<a href="https://www.treywilletto.com" target="_blank">Trey Willetto</a>.
</footer>

<style lang="scss" global>
	@import '/src/lib/styles/stylereset.css';

	@import url('https://fonts.googleapis.com/css2?family=Rubik:wght@300;400;500&display=swap');
	:root {
		font-family: 'rubik', Helvetica, sans-serif;
	}
	body {
		background-color: $blue-800;
	}
	main {
		display: grid;
		place-items: center;
		margin-top: 70px;
	}
	.attribution {
		font-size: 11px;
		text-align: center;
		margin-top: 3rem;
		color: $blue-200;
		a {
			color: $blue-300;
		}
	}
</style>
