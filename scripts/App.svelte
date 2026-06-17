<script>

	const copyableTexts = [
		'🙏',
		'🥰',
		'😍',
		'🌈',
		'✨',
		'👍',
		'😂', 
		'🤣',
		'😭'
	]


</script>

<h1>✨ Mes emoji prefs 🌈</h1>

<ul class="copyables">
	{#each copyableTexts as text}
		<li>
			<span>{text}</span>
		</li>
	{/each}
</ul>



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
			max-width: 60rem;
		}
	}

	.copyables{
		list-style: none;

		text-align: center;

		li{
			display: inline-flex;

			font-size: 6em;

			width: 1.2em;
			height: 1.2em;
			padding: 0.8em;
			margin: 0.2em;

			flex-direction: row;
			align-items: center;
			justify-content: center;

			border-radius: 10%;

			background-color: var(--secundary-background-color);

		}
	}
	
</style>
