<script>
 	import { fade, fly } from 'svelte/transition';

	const copyableTexts = [
		'🙏',
		'🥰',
		'😍',
		'🌈',
		'✨',
		'👍',
		'😂', 
		'🤣',
		'😭',
		//'👉👈'
	]

	let displayFeedbackX = $state(undefined);
	let displayFeedbackY = $state(undefined);

	let showFeeback = $state(false);

	function copy(textToCopy, e){
		navigator.clipboard
			.writeText(textToCopy)
			.then(() => {
				displayFeedbackX = e.pageX
				displayFeedbackY = e.pageY
				showFeeback = true

				setTimeout(() => {
					showFeeback = false
				}, 600)

				console.log('displayFeedbackX displayFeedbackY', displayFeedbackX, displayFeedbackY)

				console.log('Copié dans le presse-papier !', textToCopy)
			})
	}


	

</script>

<h1>✨ Mes emoji prefs 🌈</h1>

<ul class="copyables">
	{#each copyableTexts as text}
		<!-- svelte-ignore a11y_click_events_have_key_events -->
		<!-- svelte-ignore a11y_no_noninteractive_element_interactions -->
		<li onclick={(e) => copy(text, e)}>
			<span class="to-copy">{text}</span>
		</li>
	{/each}
</ul>

{#if showFeeback}
	<div 
		class={["copy-feedback"]}
		style:top={`${displayFeedbackY}px`}
		style:left={`${displayFeedbackX}px`}
		in:fly={{ y: 40, delay: 200 }} 
		out:fade={{delay: 120}}
		>
		Copié !
	</div>
{/if}


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

			border-radius: 2rem;

			background-color: var(--secundary-background-color);

			cursor: pointer;

			border: 1px solid transparent;


			&:hover, &:active{
				border-color: var(--secundary-foreground-color);
			}

		}
	}

	.copy-feedback{
		display: block;
		position: absolute;

		pointer-events: none;
		
		background-color: var(--primary-background-color);
		border: 1px solid var(--secundary-foreground-color);
		transform: translateX(-50%) translateY(-150%);
		padding: 0.5em;
		border-radius: 0.5rem;

	}
	
</style>
