<script>
    import Paper from "@smui/paper";
    import { supabase } from "../../db";
    import IconButton, { Icon } from '@smui/icon-button';
    import DOMPurify from 'dompurify';
    
    let addingContent = false;
    let value = '';
    $: customContent = [{content: ''}];

    getFromDatabase().then((data) => {
        customContent = data || [];
    });

    async function getFromDatabase() {
		let query = supabase.from('custom_content').select('content');
		const { data, error } = await query;
		if (error) console.log(error);
		console.log(data);
		/**
		 * @type {string[]}
		 */

		return data;
	}
</script>
<div>
    <Paper style="width: 100%">
        <h2>Custom Content</h2>
        <IconButton class="material-icons" on:click={() => addingContent = !addingContent}>add</IconButton>
        {#if addingContent}
            <textarea bind:value={value}></textarea>
            <IconButton class="material-icons" on:click={() => {
                let contentToPush = value;
                let safeContent = DOMPurify.sanitize(contentToPush, {USE_PROFILES: {html: true}});

                customContent.push({content: safeContent});
                value = '';
                addingContent = false;
                customContent = customContent;
                
                

                
                async function fetchData() {
                    let getContentQuery = supabase.from('custom_content').select('content');
                    let dbContent = await getContentQuery;
                    //Need to only insert content that is not in the database
                    let contentToInsert = customContent.filter((item) => {
                        return !dbContent.data?.some((dbItem) => dbItem.content === item.content);
                    });

                    let setContentQuery = supabase.from('custom_content').insert(contentToInsert);
                   
                    //Find difference between custoMContent and what is in the database
                    //If there is a difference, update the database
                    
                    const { data, error } = await setContentQuery;
                    console.log(data);
                    console.log(error);
                }

                fetchData();

            }}>save</IconButton>
        {/if}
        {#each customContent as item, i}
        <div>
            <Paper variant="outlined">
                <div class="row">

                    <p>{@html DOMPurify.sanitize(item.content, {USE_PROFILES: {html: true}})}</p>
                </div>
                
            </Paper>
            
        </div>
            
        {/each}
    </Paper>

</div>
<style>
    .row {
        display: flex;
        justify-content: space-between;
        width: 100%;
    }
</style>