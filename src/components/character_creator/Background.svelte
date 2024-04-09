<script>
	import Autocomplete from '@smui-extra/autocomplete';
	import { supabase } from '../../db';
	let background = getFromDatabase();
	/**
	 * @type {string}
	 */
	let backgroundChoice;

	async function getFromDatabase() {
		let query = supabase.from('backgrounds').select('name');
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
	<h2>Background</h2>
	<Autocomplete bind:value={backgroundChoice} options={background} label="Background" />
</div>

<style>
	div {	
		margin: 3px;
	}
</style>
