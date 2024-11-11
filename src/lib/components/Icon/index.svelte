<script>
	/**
	 * @typedef {Object} Props
	 * @property {object} [iconName] The icon itself from the icon library
	 * @property {string} [iconChar] Can be a character instead of an icon
	 * @property {boolean} [spin] Should it spin? Useful for loaders
	 * @property {string} [color] The color of the icon
	 */

	/** @type {Props} */
	let { spin = false, iconChar, color = 'var(--figma-color-icon)', iconName } = $props();
</script>

<div class={['icon', spin ? 'icon--spin' : ''].join(' ')} style="color: {color}; fill: {color}">
	{#if iconChar}
		{iconChar}
	{:else if iconName}
		{@html iconName}
	{/if}
</div>

<style>
	.icon {
		vertical-align: middle;
		width: var(--spacer-xl);
		height: var(--spacer-xl);
		display: flex;
		text-align: center;
		justify-content: center;
		align-items: center;
		font-size: var(--text-body-large-font-size);
		line-height: var(--text-body-large-font-size);
		font-weight: var(--text-body-large-font-weight);
	}
	.icon--spin {
		animation: spin 1s linear infinite;
	}
	@keyframes spin {
		from {
			transform: rotate(0deg);
		}
		to {
			transform: rotate(360deg);
		}
	}
</style>
