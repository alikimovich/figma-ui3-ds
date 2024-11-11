<script>
	import Label from '$lib/components/Label/index.svelte';
	/**
	 * @typedef {Object} Props
	 * @property {string} [value] Entered value
	 * @property {string} [placeholder] Placeholder text. According NN/g using them is not recommended. Consider using a label instead or supporting text instead.
	 * @property {string} [supportText] Supporting text to help users understand the input field and it's requirements.
	 * @property {string} [label] Label text, should be a noun
	 * @property {'text' | 'password' | 'email' | 'number'} [type]
	 * @property {boolean} [required]
	 * @property {string} [error]
	 * @property {string} [id]
	 */

	/** @type {Props} */
	let {
		value = $bindable(''),
		placeholder = '',
		supportText = '',
		label = '',
		type = 'text',
		required = false,
		error = '',
		id = ''
	} = $props();

	const inputId = $derived(id || `input-${Math.random().toString(36).slice(2)}`);
</script>

<div class="input-container">
	{#if label}
		<Label labelText={label} {inputId} />
	{/if}

	<input
		{type}
		{placeholder}
		{required}
		id={inputId}
		bind:value
		class="text-input body-lg"
		class:error
		aria-invalid={!!error}
		aria-describedby={error ? `${inputId}-error` : undefined}
	/>

	{#if supportText}
		<span class="support-text body-sm">{supportText}</span>
	{:else if error}
		<span class="error-message body-sm" id={`${inputId}-error`}>{error}</span>
	{/if}
</div>

<style>
	.input-container {
		display: flex;
		flex-direction: column;
		gap: var(--spacer-sm);
		width: 100%;
	}

	.text-input {
		border: 0 none;
		background-color: var(--figma-color-bg-secondary);
		padding: var(--spacer-md);
		outline: 1px solid var(--figma-color-bg-secondary);
		outline-offset: -1px;
		border-radius: var(--radius-medium);
		transition: outline 0.1s ease-out;
	}

	.text-input:hover {
		outline: 1px solid var(--figma-color-border);
		transition: outline 0.1s ease-out;
	}

	.text-input:focus {
		outline: 1px solid var(--figma-color-border-selected);
		transition: outline 0.1s ease-out;
	}

	.text-input.error {
		outline: 1px solid var(--figma-color-border-danger-strong);
	}

	.error-message {
		color: var(--figma-color-text-danger);
	}

	.support-text {
		color: var(--figma-color-text-secondary);
	}
</style>
