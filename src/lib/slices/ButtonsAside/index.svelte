<script lang="ts">
	import type { Content } from '@prismicio/client';
	import Button from '$lib/components/Button.svelte';

	export let slice: Content.ButtonsAsideSlice;
</script>

<aside
	data-slice-type={slice.slice_type}
	data-slice-variation={slice.variation}
	class="aside-container"
	style="--aside-margin: {slice.primary.slice_margin_bottom}rem"
>
	<div class="buttons-container">
		{#each slice.primary.buttons as item}
			<Button
				disabled={item.disabled}
				firstHalf={item.firstcharacters}
				specialChar={item.styled_character}
				secondHalf={item.last_characters}
				route={item.buttonroute}
			/>
		{/each}
	</div>
	{#if slice.primary.cta_description}
		<p class="cta-description">{slice.primary.cta_description}</p>
	{/if}
</aside>

<style>
	.aside-container {
		margin: 0 0 var(--aside-margin, 0) -0.7rem;
		width: 100vw;
	}

	.aside-container :global(p) {
		letter-spacing: -0.02em;
	}

	.buttons-container {
		display: flex;
		flex-direction: row;
		justify-content: center;
		gap: 0.4rem;
		margin: 0 0 0.9rem 0;
	}

	.cta-description {
		font-size: 0.9rem;
		font-weight: 400;
		text-align: center;
	}

	@media (max-width: 1024px) {
		.aside-container {
			width: 100%;
			margin: 0 0 var(--aside-margin, 0) 0;
		}
	}
</style>
