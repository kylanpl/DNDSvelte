<script>
    import Proficiency from "./Proficiency.svelte";
    import LayoutGrid, { Cell } from '@smui/layout-grid';

    let proficiencyArray = [
        "Acrobatics",
        "Animal Handling",
        "Arcana",
        "Athletics",
        "Deception",
        "History",
        "Insight",
        "Intimidation",
        "Investigation",
        "Medicine",
        "Nature",
        "Perception",
        "Performance",
        "Persuasion",
        "Religion",
        "Sleight of Hand",
        "Stealth",
        "Survival"
    ];
</script>

<div>
    <h2>Proficiencies</h2>

    <LayoutGrid class="profgrid">
        {#each proficiencyArray as proficiency, i}
            <Cell class="profgrid" span=5>
                <Proficiency type={proficiency} />
            </Cell>
        {/each}
      </LayoutGrid>

    
</div>

<style>
.profgrid {
    padding: 0;
}
</style>
