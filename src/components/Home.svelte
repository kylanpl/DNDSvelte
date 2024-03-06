<script>
    import Paper, {Content} from '@smui/paper'
    import Button, { Label } from '@smui/button';
    import { currentComponent } from "../stores";
</script>
<Paper class="buttons-paper">
    <Content class="buttons-content">
        <Button on:click={() => $currentComponent = 'New'} variant="raised">
            <Label>New Character</Label>
        </Button>
        <Button>
            <Label>Library</Label>
        </Button>
    </Content>
</Paper> 
<style>
:global(.buttons-paper) {
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    padding: 10px;
}
</style>

