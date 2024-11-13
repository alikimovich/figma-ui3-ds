<script>
	import Label from '$lib/components/Label/index.svelte';
	import Icon from '$lib/components/Icon/index.svelte';
	/**
	 * @typedef {Object} Props
	 * @property {any} [value] Entered value
	 * @property {string} [placeholder] Placeholder text. According to NN/g using them is not recommended. Consider using a label instead or supporting text instead.
	 * @property {string} [supportText] Supporting text to help users understand the input field and it's requirements.
	 * @property {string} [label] Label text, should be a noun
	 * @property {'text' | 'password' | 'number'  } [type]
	 * @property {boolean} [required] Is the field required?
	 * @property {string} [error]
	 * @property {string} [id]
	 * @property {string} [iconName] The svg icon itself from the icon library
	 * @property {string} [iconChar] Can be a character instead of an icon
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
		id = '',
		iconName,
		iconChar = ''
	} = $props();

	const inputId = $derived(id || `input-${Math.random().toString(36).slice(2)}`);
</script>

<div class="input-container flex column gap-sm">
	{#if label}
		<Label labelText="{label}{required ? '*' : ''}" {inputId} />
	{/if}
	<div
		class="input-panel body-md flex row gap-sm align-items-center {iconName || iconChar
			? ''
			: 'pl-md'}"
		class:error
	>
		{#if iconName || iconChar}
			<Icon {iconName} {iconChar} color="var(--figma-color-icon-secondary)" />
		{/if}
		<input
			{type}
			{placeholder}
			{required}
			id={inputId}
			bind:value
			class="text-input body-md"
			aria-invalid={!!error}
			aria-describedby={error ? `${inputId}-error` : undefined}
		/>
	</div>

	{#if error}
		<span class="error-message body-sm" id={`${inputId}-error`}>{error}</span>
	{:else if supportText}
		<span class="support-text body-sm">{supportText}</span>
	{/if}
</div>

<style>
	.input-container {
		width: 100%;
	}
	.input-panel {
		border: 0 none;
		background-color: var(--figma-color-bg-secondary);
		outline: 1px solid var(--figma-color-bg-secondary);
		outline-offset: -1px;
		border-radius: var(--radius-medium);
		transition: outline 0.1s ease-out;
		width: 100%;
		height: 1.5rem;
	}

	.input-panel:hover {
		outline: 1px solid var(--figma-color-border);
	}

	.input-panel:focus-within {
		outline: 1px solid var(--figma-color-border-selected);
	}

	.input-panel.error {
		outline: 1px solid var(--figma-color-border-danger-strong);
	}

	.text-input {
		border: 0 none;
		padding: 0;
		height: 1.5rem;
		background-color: transparent;
		width: 100%;
		outline: 0 none;
	}

	.error-message {
		color: var(--figma-color-text-danger);
	}

	.support-text {
		color: var(--figma-color-text-secondary);
	}
</style>
