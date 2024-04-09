<script>
	import Autocomplete from '@smui-extra/autocomplete';
	import { supabase } from '../../db';
	let classes = getFromDatabase();

	async function getFromDatabase() {
		let query = supabase.from('classes').select('name');
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
		return classes;
	}
</script>

<div>
	<h2>Class</h2>
	<Autocomplete options={classes} label="Class" />
</div>

<style>
	div {
		margin: 3px;
	}
</style>
