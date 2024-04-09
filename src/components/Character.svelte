<script>
    import Tab, { Label } from '@smui/tab';
    import TabBar from '@smui/tab-bar';
    import Card, { Actions } from '@smui/card';
    import Textfield from '@smui/textfield';
    import Paper from '@smui/paper';
    let sub_active = 'Race';
    let active = 'Options';
    import Races from './character_menu/Races.svelte';
    import AbilityScores from './character_creator/AbilityScores.svelte';
    import Feats from './character_menu/Feats.svelte';
	import Proficiencies from './character_creator/Proficiencies.svelte';
    import Backgrounds from './character_menu/Backgrounds.svelte';
    import Spells from './character_menu/Spells.svelte';
    import Inventory from './character_menu/Inventory.svelte';
    import CustomContent from './character_menu/CustomContent.svelte';
</script>

<div class="character-window-container">
    <div class="character-window">
        <Paper>
            <div class="row">
                <div class="side-container">

        
                <TabBar tabs={['Options', 'Demographic']} let:tab bind:active>
                    <Tab {tab} >
                        <Label>{tab}</Label>
                    </Tab>
                </TabBar>

                {#if active == 'Demographic'}
                <Paper variant="outlined">
                    <Textfield value="" label="Character Name"></Textfield>
                    <Textfield value="" label="Experience" type=number></Textfield>
                    <Textfield value="" label="Image URL" style="width: 100%"></Textfield>
                    <div class="row">
                        <Textfield value="" label="Age"></Textfield>
                        <Textfield value="" label="Gender"></Textfield>
                        <Textfield value="" label="Height"></Textfield>
                        <Textfield value="" label="Weight"></Textfield>
                    </div>
                    <div class="row">
                        <div>
                            <Textfield value="" label="Hair Color"></Textfield>
                        </div>
                        
                        <Textfield value="" label="Eye Color"></Textfield>
                        <Textfield value="" label="Skin Color"></Textfield>
                    </div>

                    <div class="row">
                        <Textfield value="" label="Personality Trait 1"></Textfield>
                        <Textfield value="" label="Personality Trait 2"></Textfield>
                    </div>
                    <div>
                        <Textfield textarea value="" label="Ideals" style="width: 100%; margin: 5px 0 5px 0;"></Textfield>
                    </div>
                    <Textfield textarea value="" label="Bonds"   style="width: 100%; margin: 5px 0 5px 0;"></Textfield>
                    <Textfield textarea value="" label="Flaws"   style="width: 100%; margin: 5px 0 5px 0;"></Textfield>
                    
                    <Textfield textarea value="" label="Backstory" style="width: 100%; margin: 5px 0 5px 0;"></Textfield>
        
                </Paper>
                {:else}
                <Paper variant="outlined">
                    <TabBar tabs={['Race', 'Class\n/\nLevel', 'Ability Scores / Feats', 'Background', 'Proficiencies', 'Spells', 'Inventory']} let:tab bind:active>
                        <Tab {tab} minWidth class="sub_tabs" style="padding: 0 3% 0 3%;"  >
                            <Label style="font-size: 70%" >{tab}</Label>
                        </Tab>
                    </TabBar>
                    <!-- svelte-ignore empty-block -->
                    <div class="subtab-content">
                    {#if active == 'Race'}
                    <Races />
                    {:else if active == 'Class\n/\nLevel'}

                    {:else if active == 'Ability Scores / Feats'}
                        <Paper>
                            <AbilityScores />
                        </Paper>
                        <Paper >
                            <Feats />
                        </Paper>
                    {:else if active == 'Background'}
                        <Backgrounds />
                    {:else if active == 'Proficiencies'}
                        <Proficiencies />
                    {:else if active == 'Spells'}
                        <Spells />
                    {:else if active == 'Inventory'}
                        <Inventory />
                    {/if}
                    </div>
                </Paper>
                {/if}
                </div>
                <div style="margin-left: 5%">
                    <CustomContent />
                </div>
            </div>
        </Paper>

</div>


    
</div>

<style>

    .subtab-content {
        display: flex;
        flex-direction: column;
        align-items: center;
        margin: auto;
    }
    :global(.character-window-container) {
        margin: 5%;
    }

    :global(.character-window) {

        margin: auto;
    ;
    }

    .row {
        display: flex;
        flex-direction: row;

    }


    .side-container {
        display: flex;
        flex-direction: column;
        width: 48%;
    }

    :global(.sub_tabs *) {
        display: flex;
        padding: 0px;
    }

  

</style>