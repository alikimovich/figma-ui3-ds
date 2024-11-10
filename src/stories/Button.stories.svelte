<script module>
	import { defineMeta, setTemplate, type Args } from '@storybook/addon-svelte-csf';
	import { Button } from '$lib/components';
	import { fn } from '@storybook/test';

	const { Story } = defineMeta({
		title: 'Design System/Buttons/Button',
		component: Button,
		tags: ['autodocs'],
		argTypes: {
			type: {
				control: { type: 'select' },
				options: ['primary', 'secondary', 'tertiary'],
				defaultValue: 'primary'
			},
			size: {
				control: { type: 'select' },
				options: ['small', 'medium', 'large']
			}
		},
		args: {
			type: 'primary',
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

<Story name="Primary" args={{ type: 'primary', label: 'Verb' }} />

<Story name="Secondary" args={{ type: 'secondary', label: 'Verb' }} />

<Story name="Tertiary" args={{ type: 'tertiary', label: 'Verb' }} />
