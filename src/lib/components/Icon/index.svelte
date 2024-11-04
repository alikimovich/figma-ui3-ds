<script>
	/**
	 * @typedef {Object} Props
	 * @property {boolean} [spin] Should it spin? Useful for loaders
	 * @property {any} [children] Can be text or an icon
	 */

	/** @type {Props} */
	const { spin = false, children } = $props();
</script>

<div class={['icon', spin ? 'icon--spin' : ''].join(' ')}>{@render children?.()}</div>

<style>
	.icon {
		display: inline-block;
		vertical-align: middle;
		width: var(--spacer-xl);
		height: var(--spacer-xl);
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
