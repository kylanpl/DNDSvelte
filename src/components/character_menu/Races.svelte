<script>

    import LayoutGrid, { Cell } from '@smui/layout-grid';
    import { supabase } from "../../db";
    import Radio from '@smui/radio';
    import FormField from '@smui/form-field';
    /**
   * @type {string}
   */
    export let selected = '';


    $: options = [''];
    getFromDatabase().then((data) => {
        options = data;
    });

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
    <LayoutGrid class="profgrid">
        {#each options as option, i}
            <Cell class="profgrid" style="border: 2px solid #FF3E00; padding-right: 20px; border-radius: 5px;" span=5>
                <div>
                    <FormField>
                    <Radio bind:group={selected} value={option} />
                    <span slot="label">{option}</span>
                  </FormField>
                </div>
            </Cell>
        {/each}
      </LayoutGrid>

    
</div>

<style>

</style>




