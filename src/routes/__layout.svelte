<script context="module" lang="ts">
	import { waitLocale, _, isLoading } from 'svelte-i18n';
	import '../i18n';

	export async function preload() {
		// awaits for the loading of the 'en-US' and 'en' dictionaries
		return waitLocale();
	}
</script>

<script lang="ts">
	import Header from '$lib/header.svelte';
	import '../app.css';
</script>

{#if $isLoading}
	<p>Loading...</p>
{:else}
	<Header />

	<main>
		<slot />
	</main>

	<footer>
		<p>
			{$_('footer.copyright')} <a href="https://www.satsuma.se">Satsuma Studios</a>
		</p>
	</footer>
{/if}

<style>
	main {
		flex: 1;
		display: flex;
		flex-direction: column;
		padding: 1rem;
		width: 100%;
		max-width: 1024px;
		margin: 0 auto;
		box-sizing: border-box;
	}

	footer {
		display: flex;
		flex-direction: column;
		justify-content: flex-end;
		align-items: flex-end;
		padding-right: 1em;
		font-size: 0.9rem;
	}

	footer a {
		font-weight: bold;
	}
</style>
