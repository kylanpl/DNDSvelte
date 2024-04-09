
<div>
    <FormField>
    <Checkbox bind:checked />
    <span slot="label">{type}</span>
  </FormField>
</div>

<style>
</style>

<script>
    import Checkbox from '@smui/checkbox';
    import FormField from '@smui/form-field';
  
    let checked = false;
    /**
   * @type {string}
   */
    export let type;
</script>
