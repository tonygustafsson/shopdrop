<script lang="ts">
	import { searchValue } from '../../stores/items';
	import Button from '$lib/button.svelte';
	import { _ } from 'svelte-i18n';
	import Textfield from '$lib/textfield.svelte';

	const setSearchValue = (e) => {
		// Update the search value on blur
		searchValue.set(e.target.value.toLowerCase());
	};

	const clearSearch = () => {
		searchValue.set('');
	};
</script>

<form on:submit={(e) => e.preventDefault()} class="search-form">
	<label for="search">{$_('planning.search_label')}</label>
	<div>
		<Textfield
			type="search"
			id="search"
			name="search"
			class="search-input"
			value={$searchValue}
			onKeyUp={setSearchValue}
		/>
	</div>
	<Button type="submit">{$_('planning.search_cta')}</Button>
	<Button type="button" on:click={clearSearch}>{$_('planning.search_clear')}</Button>
</form>

<style>
	.search-form {
		margin-bottom: 1.5em;
	}
</style>
