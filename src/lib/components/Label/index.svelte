<script>
	/**
	 * @typedef {Object} Props
	 * @property {string} [labelText] The text to display
	 * @property {string} [inputId] The id of the input element this label is for
	 */

	/** @type {Props} */
	let { labelText, inputId } = $props();
</script>

<label class="body-md" for={inputId}>
	{labelText}
</label>

<style>
	label {
		color: var(--figma-color-text-secondary);
	}
</style>
