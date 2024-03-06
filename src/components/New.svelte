<script>
// @ts-nocheck

	import Paper, { Content } from "@smui/paper";
	import { Section } from "@smui/top-app-bar";
    import Textfield from '@smui/textfield';
    import HelperText from '@smui/textfield/helper-text';
	import { Label } from "@smui/common";
    import Card, { Actions } from '@smui/card';
    import Demographic from "./character_creator/Demographic.svelte"
	import Button from "@smui/button";
    import Class from "./character_creator/Class.svelte";


    let page = 0;

    const CharacterCreatorPages = {
        0 : Demographic,
        1 : Class,
    }


</script>


<div class="creator-window">
    <h1>Character Creator</h1>
        <Card padded >

            <svelte:component this={CharacterCreatorPages[page]} />
            {#if page == 0}
            <Actions class="next">
                <Button on:click={ () => page++}>
                    <i class="material-icons test" aria-hidden="true">arrow_forward</i>
                </Button>
            </Actions>
            {:else}
            <Actions class="next-back">
                <Button on:click={ () => page--}>
                    <i class="material-icons" aria-hidden="true">arrow_backward</i>
                </Button>
                <Button on:click={ () => page++}>
                    <i class="material-icons" aria-hidden="true">arrow_forward</i>
                </Button>
            </Actions>
            {/if}

        </Card>
</div>

<style>
    :global(.creator-window) {
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    }

    :global(.next) {
    justify-content: right;
    }

    :global(.next-back) {
    justify-content: space-between;
    }
</style>