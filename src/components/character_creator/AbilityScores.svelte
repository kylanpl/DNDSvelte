<script>
	import Textfield from '@smui/textfield';
	import Autocomplete from '@smui-extra/autocomplete';
	import Stat from './Stat.svelte';
	import Button, { Label } from '@smui/button';
	import HelperText from '@smui/textfield/helper-text';

	$: stats = [
		{name: 'STR', value: 0},
		{name: 'DEX', value: 0},
		{name: 'CON', value: 0},
		{name: 'INT', value: 0},
		{name: 'WIS', value: 0},
		{name: 'CHA', value: 0}
	];


	function generateStat() {
		let generated = [];
		for (let i = 0; i < 4; i++) {
			generated.push(Math.floor(Math.random() * 6) + 1);
		}
		generated.sort();
		generated.shift();
		return generated.reduce((a, b) => a + b, 0);
	}
	function randChar() {
		stats.forEach((stat) => {
			stat.value = generateStat();
		});
		stats = [...stats];
	}

	/**
	 * @param {number} input
	 */
	function getMod(input) {
		let number = Math.floor((Number(input) - 10) / 2);
		return Number(number) >= 0 ? `+${number}` : number
	}

	export let displayHeader = false;
</script>

<div class="center">
	{#if displayHeader}
		<h1>Ability Scores</h1>
	{/if}


	<div id="stat-container">

	{#each stats as stat}
		<div class="column">
			<Textfield style="width: 50px;" bind:value={stat.value} label="" type="number" input$max="20" input$min="0">
				<HelperText persistent slot="helper">{stat.name.toUpperCase()}</HelperText>
			</Textfield>
			<p>{getMod(stat.value)}</p>
		</div>
	{/each}
	</div>

	<div class="randchar">
		<Button title="4d6, drop the lowest." on:click={() => randChar()}>
			<Label align="left">Random</Label>
		</Button>
	</div>
</div>

<style>
	#stat-container {
		display: flex;
		flex-direction: row;
	}

	.column {
		display: flex;
		flex-direction: column;
	}

	.randchar {
		position: relative;
		left: 30%

	}



</style>
