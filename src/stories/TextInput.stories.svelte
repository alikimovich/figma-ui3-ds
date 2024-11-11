<script module>
	import { defineMeta, setTemplate, type Args } from '@storybook/addon-svelte-csf';
	import { TextInput } from '$lib/components';
	import { IconComponent } from '$lib/icons';

	const { Story } = defineMeta({
		title: 'Design System/Inputs/TextInput',
		component: TextInput,
		tags: ['autodocs'],
		argTypes: {
			label: {
				control: { type: 'text' },
				defaultValue: 'Noun'
			},
			supportText: {
				control: { type: 'text' },
				defaultValue: ''
			},
			placeholder: {
				control: { type: 'text' },
				defaultValue: 'Placeholder texts are harmful'
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
				type: 'object',
				defaultValue: IconComponent
			},
			iconChar: {
				control: { type: 'text' }
			},
			type: {
				control: { type: 'select' },
				options: ['text', 'password'],
				defaultValue: 'text'
			},
			error: { control: { type: 'text' } }
		},
		args: {
			type: 'text',
			label: 'Noun',
			placeholder: 'Placeholder texts are harmful'
		}
	});
</script>

<script lang="ts">
	setTemplate(template);
</script>

{#snippet template({ ...args }: Args<typeof Story>)}
	<TextInput {...args} />
{/snippet}

<Story
	name="Primary"
	args={{
		type: 'text',
		required: false,
		supportText: 'Field requirements',
		iconName: IconComponent
	}}
/>

<Story name="Error" args={{ type: 'text', label: 'Noun', error: 'Error!', required: true }} />
