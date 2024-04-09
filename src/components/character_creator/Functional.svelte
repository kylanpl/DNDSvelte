<script>
	import AbilityScores from './AbilityScores.svelte';
	import Race from './Race.svelte';
	import Class from './Class.svelte';
	import Background from './Background.svelte';
	import Proficiencies from './Proficiencies.svelte';
</script>

<div>
	<div class="row">
		<div class="column">
			<div class="row">
				<Class />
				<Race />
                <Background />
			</div>
			<div class="row ability-scores">
				<AbilityScores />
                <Proficiencies />
			</div>
            <div>
                
            </div>
        </div>
	</div>
</div>

<style>
	.row {
		display: flex;
	}

	.column {
		display: flex;
		flex-direction: column;
	}
</style>
