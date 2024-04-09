<script>
	import Textfield from '@smui/textfield';
	import HelperText from '@smui/textfield/helper-text';
	/**
	 * @type {string}
	 */
	export let statString = '';
	/**
	 * @type {number}
	 */
	export let value;

	export function randChar() {}
</script>

<div>
	<div>
		<p>
			<Textfield style="width: 50px" bind:value label="" type="number">
				<HelperText persistent slot="helper">{statString.toUpperCase()}</HelperText>
			</Textfield>
		</p>
	</div>
</div>

<style>
	* {
		margin: 0;
	}
</style>
