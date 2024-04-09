<script>
	import Textfield from '@smui/textfield';
	import Autocomplete from '@smui-extra/autocomplete';

	let alignments = [
		'Lawful Good',
		'Lawful Neutral',
		'Lawful Evil',
		'Neutral Good',
		'True Neutral',
		'Neutral Evil',
		'Chaotic Good',
		'Chaotic Neutral',
		'Chaotic Evil'
	];
</script>
<div>
	<h2>Description</h2>
	<Textfield value="" label="Name"></Textfield>
	<div>
		<Textfield value="" type="number" label="Age"></Textfield>
		<Textfield value="" label="Gender"></Textfield>
	</div>
	<div>
		<Textfield value="" label="Height"></Textfield>
		<Textfield value="" label="Weight"></Textfield>
	</div>
	<Autocomplete options={alignments} label="Alignment" />	
</div>

<style>

</style>
