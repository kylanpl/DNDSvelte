<script>
    import { currentComponent } from '../stores.js'

    import Home from '../components/Home.svelte'
    import New from '../components/New.svelte'
    /**
	 * @type {typeof Home}
	 */
    let CurrentComp;

    $: {
        if ($currentComponent === 'Home') {
        CurrentComp = Home;
      }
        else if ($currentComponent === 'New') {
        CurrentComp = New;
        }
    }
    
</script>


<svelte:component this={CurrentComp} />