<script module>
	import { defineMeta, setTemplate, type Args } from '@storybook/addon-svelte-csf';
	import { IconButton } from '$lib/components';
	import { IconComponent } from '$lib/icons';
	import { fn } from '@storybook/test';

	const { Story } = defineMeta({
		title: 'Design System/Buttons/IconButton',
		component: IconButton,
		tags: ['autodocs'],
		argTypes: {
			type: {
				control: { type: 'select' },
				options: ['primary', 'secondary', 'tertiary'],
				defaultValue: 'primary'
			},
			iconName: {
				type: 'object',
				defaultValue: 'IconComponent'
			},
			iconChar: {
				control: { type: 'text' }
			},
			onClick: {
				control: { type: 'function' },
				defaultValue: fn()
			}
		}
	});
</script>

<script lang="ts">
	setTemplate(template);
</script>

{#snippet template({ ...args }: Args<typeof Story>)}
	<IconButton iconName={IconComponent} {...args} />
{/snippet}

<Story name="Primary" args={{ type: 'primary' }} />

<Story name="Secondary" args={{ type: 'secondary' }} />

<Story name="Tertiary" args={{ type: 'tertiary' }} />
