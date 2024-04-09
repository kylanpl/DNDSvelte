<script>
	// @ts-nocheck

	import Paper, { Content } from '@smui/paper';
	import { Section } from '@smui/top-app-bar';
	import Textfield from '@smui/textfield';
	import HelperText from '@smui/textfield/helper-text';
	import { Label } from '@smui/common';
	import Card, { Actions } from '@smui/card';
	import Demographic from './character_creator/Demographic.svelte';
	import Button from '@smui/button';
	import Class from './character_creator/Class.svelte';

	import Functional from './character_creator/Functional.svelte';
	import AbilityScores from './character_creator/AbilityScores.svelte';
	import { currentComponent } from '../stores';

	let page = 0;

	const CharacterCreatorPages = {
		0: Demographic,
		1: Functional,
		2: AbilityScores
	};
</script>

<div class="creator-window-container">
	<h1	h1>Character Creator</h1>
	<div class="creator-window">
	<Card padded>
		<svelte:component this={CharacterCreatorPages[page]} />
		{#if page == 0}
			<Actions class="next">
				<Button on:click={() => page++}>
					<i class="material-icons test" aria-hidden="true">arrow_forward</i>
				</Button>
			</Actions>
		{:else if page < CharacterCreatorPages.length - 1}
			<Actions class="next-back">
				<Button on:click={() => page--}>
					<i class="material-icons" aria-hidden="true">arrow_backward</i>
				</Button>
				<Button on:click={() => page++}>
					<i class="material-icons" aria-hidden="true">arrow_forward</i>
				</Button>
			</Actions>
		{:else}
			<Actions class="next-back">
				<Button on:click={() => page--}>
					<i class="material-icons" aria-hidden="true">arrow_backward</i>
				</Button>
				<Button on:click={() => $currentComponent = 'Home'}>
					<i class="material-icons" aria-hidden="true">done</i>
				</Button>
			</Actions>
		{/if}

	</Card>
	</div>
</div>

<style>

	:global(.creator-window-container) {
		display: flex;
		flex-direction: column;
	}
	:global(.creator-window) {
		display: flex;
        margin: auto;
	}

	:global(.next) {
		justify-content: right;
	}

	:global(.next-back) {
		justify-content: space-between;
	}
</style>
