<script>
	import Label from '$lib/components/Label/index.svelte';
	import Icon from '$lib/components/Icon/index.svelte';
	/**
	 * @typedef {Object} Props
	 * @property {any} [value] Selected value
	 * @property {{value: any, label: string}[]} [options] Array of options
	 * @property {string} [supportText] Supporting text to help users understand the input field and it's requirements.
	 * @property {string} [label] Label text, should be a noun
	 * @property {boolean} [required] Is the field required?
	 * @property {string} [error]
	 * @property {string} [id]
	 * @property {string} [iconName] The svg icon itself from the icon library
	 * @property {string} [iconChar] Can be a character instead of an icon
	 */

	/** @type {Props} */
	let {
		value = $bindable(''),
		supportText = '',
		label = '',
		options = [
			{ value: '', label: 'Select an option' },
			{ value: 'coffee', label: 'Coffee' },
			{ value: 'tea', label: 'Tea' },
			{ value: 'water', label: 'Water' }
		],
		required = false,
		error = '',
		id = '',
		iconName,
		iconChar = ''
	} = $props();

	const inputId = $derived(id || `input-${Math.random().toString(36).slice(2)}`);
</script>

<div class="select-container flex column gap-sm">
	{#if label}
		<Label labelText="{label}{required ? '*' : ''}" {inputId} />
	{/if}
	<div
		class="select-panel body-md flex row align-items-center {iconName || iconChar ? '' : 'pl-md'}"
		class:error
	>
		{#if iconName || iconChar}
			<div class="select-icon">
				<Icon {iconName} {iconChar} color="var(--figma-color-icon-secondary)" />
			</div>
		{/if}
		<select
			{required}
			id={inputId}
			bind:value
			class="select-input body-md"
			aria-invalid={!!error}
			aria-describedby={error ? `${inputId}-error` : undefined}
		>
			{#each options as option}
				<option value={option.value}>{option.label}</option>
			{/each}
		</select>
	</div>

	{#if error}
		<span class="error-message body-sm" id={`${inputId}-error`}>{error}</span>
	{:else if supportText}
		<span class="support-text body-sm">{supportText}</span>
	{/if}
</div>

<style>
	.select-container {
		width: 100%;
	}
	.select-panel {
		border: 0 none;
		background-color: var(--figma-color-bg-secondary);
		outline: 1px solid var(--figma-color-bg-secondary);
		outline-offset: -1px;
		border-radius: var(--radius-medium);
		transition: outline 0.1s ease-out;
		width: 100%;
		height: 1.5rem;
	}
	/* .select-icon {
		position: absolute;
	} */
	.select-panel:hover {
		outline: 1px solid var(--figma-color-border);
	}

	.select-panel:focus-within {
		outline: 1px solid var(--figma-color-border-selected);
	}

	.select-panel.error {
		outline: 1px solid var(--figma-color-border-danger-strong);
	}

	.select-input {
		--webkit-appearance: none;
		--moz-appearance: none;
		appearance: none;
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
