<script module>
	import { defineMeta, setTemplate, type Args } from '@storybook/addon-svelte-csf';
	import { Button } from '$lib/components/index';
	import { fn } from '@storybook/test';

	const { Story } = defineMeta({
		title: 'Atoms/Button',
		component: Button,
		tags: ['autodocs'],
		argTypes: {
			size: {
				control: { type: 'select' },
				options: ['small', 'medium', 'large']
			}
		},
		args: {
			primary: true,
			size: 'medium',
			label: 'Verb',
			onClick: fn()
		}
	});
</script>

<script lang="ts">
	setTemplate(template);
</script>

{#snippet template({ ...args }: Args<typeof Story>)}
	<Button {...args} />
{/snippet}

<!-- It's not recommended to have more than one primary button per screen/area -->
<Story name="Primary" args={{ primary: true, label: 'Verb' }} />

<!-- Consider using a secondary button for more subtle actions -->
<Story name="Secondary" args={{ primary: false, label: 'Verb' }} />
