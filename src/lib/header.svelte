<script lang="ts">
	import { settings } from '../stores/settings';
	import { page } from '$app/stores';
	import IconGear from '$lib/icons/gear.svelte';
	import { _ } from 'svelte-i18n';
</script>

<header>
	<div class="logo">
		<h1 class="heading">
			<a href="/">Milk &amp; Eggs</a>
		</h1>
	</div>

	<div class="main-nav">
		{#if $settings.listId}
			<nav>
				<ul>
					<li class:active={$page.path === '/'}>
						<a href="/">{$_('list.title')}</a>
					</li>
					<li class:active={$page.path === '/planning'}>
						<a href="/planning">{$_('planning.title')}</a>
					</li>
				</ul>
			</nav>
		{/if}
	</div>

	<div class="tool-bar">
		<nav>
			<ul>
				<li class:active={$page.path === '/settings'}>
					<a href="/settings">
						<IconGear />
					</a>
				</li>
			</ul>
		</nav>
	</div>
</header>

<style>
	header {
		display: flex;
		flex-wrap: nowrap;
		justify-content: space-between;
		background: #000;
	}

	.logo {
		flex: 2 0 140px;
		display: flex;
		justify-content: flex-start;
		align-items: center;
	}

	.main-nav {
		flex: 10 0 0;
		display: flex;
		justify-content: center;
		align-items: center;
		font-family: var(--heading-font);
	}

	.tool-bar {
		flex: 1 0 30px;
		display: flex;
		justify-content: center;
		align-items: center;
	}

	h1 a {
		color: #fff;
	}

	h1 a:hover {
		color: #fff;
		text-decoration: none;
	}

	.heading {
		font-size: 2rem;
		margin: 12px;
		color: #fff;
	}

	nav {
		display: flex;
		justify-content: center;
	}

	.tool-bar nav {
		justify-content: flex-end;
	}

	ul {
		position: relative;
		padding: 0;
		margin: 0;
		height: 3em;
		display: flex;
		justify-content: center;
		align-items: center;
		list-style: none;
		background: var(--background);
		background-size: contain;
	}

	li {
		position: relative;
		height: 100%;
	}

	li.active::before {
		--size: 8px;
		content: '';
		width: 0;
		height: 0;
		position: absolute;
		top: -5px;
		left: calc(50% - var(--size));
		border: var(--size) solid transparent;
		border-top: var(--size) solid var(--primary-color);
	}

	nav a {
		display: flex;
		height: 100%;
		align-items: center;
		padding: 0 0.75em;
		color: #fff;
		font-weight: 700;
		text-transform: uppercase;
		letter-spacing: 10%;
		text-decoration: none;
		transition: color 0.2s linear;
	}

	a:hover {
		color: var(--primary-color);
	}

	@media (max-width: 600px) {
		header {
			flex-wrap: wrap;
		}

		.logo {
			width: 100%;
			flex-basis: 100%;
			font-size: 1.5rem;
		}

		nav {
			width: 100%;
			justify-content: flex-start;
		}

		li.active::before {
			top: auto;
			bottom: 0;
			left: calc(50% - var(--size));
			border: var(--size) solid transparent;
			border-bottom: var(--size) solid var(--primary-color);
		}
	}
</style>
