<script module>
	import { defineMeta, setTemplate, type Args } from '@storybook/addon-svelte-csf';

	import { Select } from '$lib/components/index.js';
	import { IconComponent } from '$lib/icons/index.js';

	const { Story } = defineMeta({
		title: 'Design System/Inputs/Select',
		component: Select,
		tags: ['autodocs'],
		argTypes: {
			label: {
				control: { type: 'text' },
				defaultValue: 'Noun'
			},
			options: {
				control: { type: 'object' },
				defaultValue: [
					{ value: '', label: 'Select an option' },
					{ value: 'coffee', label: 'Coffee' },
					{ value: 'tea', label: 'Tea' },
					{ value: 'water', label: 'Water' }
				]
			},
			supportText: {
				control: { type: 'text' },
				defaultValue: ''
			},
			required: {
				control: 'boolean',
				defaultValue: false
			},
			value: {
				control: { type: 'text' },
				defaultValue: ''
			},
			iconName: {
				control: { type: 'select' },
				options: [IconComponent, null],
				defaultValue: IconComponent
			},
			iconChar: {
				control: { type: 'text' }
			},
			error: { control: { type: 'text' } }
		},
		args: {
			label: 'Noun',
			placeholder: 'Placeholder texts are harmful'
		}
	});
</script>

<script lang="ts">
	setTemplate(template);
</script>

{#snippet template({ ...args }: Args<typeof Story>)}
	<Select {...args} />
{/snippet}

<Story
	name="Primary"
	args={{
		required: false,
		supportText: 'Field requirements'
	}}
/>

<Story name="Error" args={{ label: 'Noun', error: 'Error!', required: true }} />
