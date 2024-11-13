<script module>
	import { defineMeta, setTemplate, type Args } from '@storybook/addon-svelte-csf';

	import { TextInput } from '$lib/components/index.js';
	import { IconComponent } from '$lib/icons/index.js';

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
				control: { type: 'select' },
				options: [IconComponent, null],
				defaultValue: IconComponent
			},
			iconChar: {
				control: { type: 'text' }
			},
			type: {
				control: { type: 'select' },
				options: ['text', 'password', 'number'],
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
		supportText: 'Field requirements'
	}}
/>

<Story name="Error" args={{ type: 'text', label: 'Noun', error: 'Error!', required: true }} />
