<script>
	import Autocomplete from '@smui-extra/autocomplete';
	import { supabase } from '../../db';
	let races = getFromDatabase();
	/**
	 * @type {string}
	 */
	let raceChoice;

	async function getFromDatabase() {
		let query = supabase.from('races').select('name');
		const { data, error } = await query;
		if (error) console.log(error);
		console.log(data);
		/**
		 * @type {string[]}
		 */
		let classes = [];
		data?.forEach((item) => {
			classes.push(item.name.charAt(0).toUpperCase() + item.name.slice(1));
		});
		console.log(classes);
		return classes;
	}
</script>

<div>
	<h2>Race</h2>
	<Autocomplete bind:value={raceChoice} options={races} label="Race" />
	{#if raceChoice}
		<p>TODO: Implement subraces</p>
	{/if}
</div>

<style>
	div {
		margin: 3px;
	}
</style>
