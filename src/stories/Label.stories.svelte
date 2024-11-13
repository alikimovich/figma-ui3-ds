<script module>
	import { defineMeta, setTemplate, type Args } from '@storybook/addon-svelte-csf';

	import { Label } from '$lib/components/index.js';

	const { Story } = defineMeta({
		title: 'Design System/Atoms/Label',
		component: Label,
		tags: ['autodocs'],
		argTypes: {
			labelText: {
				control: { type: 'text' },
				defaultValue: 'Noun'
			}
		}
	});
</script>

<script lang="ts">
	setTemplate(template);
</script>

{#snippet template({ ...args }: Args<typeof Story>)}
	<Label {...args} />
{/snippet}

<Story name="Static" args={{ labelText: 'Input field' }} />
