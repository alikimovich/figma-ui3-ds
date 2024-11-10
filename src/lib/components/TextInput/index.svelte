<script>
	/**
	 * @typedef {Object} Props
	 * @property {string} [value]
	 * @property {string} [placeholder]
	 * @property {string} [label]
	 * @property {'text' | 'password' | 'email' | 'number'} [type]
	 * @property {boolean} [required]
	 * @property {string} [error]
	 * @property {string} [id]
	 */

	/** @type {Props} */
	let {
		value = $bindable(''),
		placeholder = '',
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
		<label for={inputId}>{label}</label>
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

	{#if error}
		<span class="error-message body-md" id={`${inputId}-error`}>{error}</span>
	{/if}
</div>

<style>
	.input-container {
		display: flex;
		flex-direction: column;
		gap: 0.5rem;
		width: 100%;
	}

	label {
		font-size: 0.875rem;
		font-weight: 500;
		color: #374151;
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
</style>
