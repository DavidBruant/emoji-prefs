<script>
	let { name } = $props();
</script>

<h2>Hello {name}! 🧝🏿</h2>

<style lang="scss">
	
	:root{
		--primary-background-color: #090040;
		--secundary-background-color:  #471396;

		--primary-foreground-color: #FFCC00;
		--secundary-foreground-color: #B13BFF;

		@media (prefers-color-scheme: light) {
			
			--primary-background-color: #DFD0B8;
			--secundary-background-color: #B13BFF;

			--primary-foreground-color: #090040;
			--secundary-foreground-color:  #471396;

		}

	}

	:global(body){
		background-color: var(--primary-background-color);
		color: var(--primary-foreground-color);
		border-color: var(--primary-foreground-color);
	}

	:global(main) {
		text-align: left;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;

		@media (min-width: 640px) {
			max-width: 70rem;
		}
	}

	h2 {
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}
	
</style>
