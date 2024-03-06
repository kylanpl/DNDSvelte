<script>
    import '../app.css';
    import Button, {Label} from '@smui/button'
    import { currentComponent } from "../stores";
    import TopAppBar, { Row, Section, Title } from '@smui/top-app-bar';
	import { goto } from '$app/navigation';
	import { redirect } from '@sveltejs/kit';
    let prominent = false;
    let dense = true;
    let secondaryColor = false;
</script>


<!-- Hint where we get fonts from. -->
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" />

<!-- Material Icons, Roboto, and Roboto Mono fonts -->
<link
  href="https://fonts.googleapis.com/css2?family=Material+Icons&Roboto+Mono:ital@0;1&family=Roboto:ital,wght@0,100;0,300;0,400;0,500;0,700;0,900;1,100;1,300;1,400;1,500;1,700;1,900&display=swap"
  rel="stylesheet"
/>

<link
  rel="stylesheet"
  href="node_modules/svelte-material-ui/themes/svelte.css"
  media="(prefers-color-scheme: light)"
/>
<link
  rel="stylesheet"
  href="node_modules/svelte-material-ui/themes/svelte-dark.css"
  media="screen and (prefers-color-scheme: dark)"
/>

    <TopAppBar variant="static"
    {prominent}
    {dense}
    color={secondaryColor ? 'secondary' : 'primary'}>
        <Row>
            <Section>
                <Button color="secondary" on:click={() => $currentComponent = 'Home'}>
                    <Label>DNDSvelte</Label>
                </Button>
            </Section>
            <Section align="end">
                <Button color="secondary" on:click={() => console.log("hi")}>
                    <Label>Kylan Plunk</Label>
                </Button>
            </Section>

        </Row>
    </TopAppBar> 

<slot></slot>

<style>
* {
    font-family: Robotom, system-ui, -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
}
</style>