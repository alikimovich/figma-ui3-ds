<script module>
	import { defineMeta, setTemplate, type Args } from '@storybook/addon-svelte-csf';
	import { TextInput } from '$lib/components';

	const { Story } = defineMeta({
		title: 'Design System/Inputs/TextInput',
		component: TextInput,
		tags: ['autodocs'],
		argTypes: {
			label: { control: { type: 'text' } },
			supportText: { control: { type: 'text' }, defaultValue: '' },
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
				efaultValue: ''
			},
			type: {
				control: { type: 'select' },
				options: ['text', 'password', 'email', 'number'],
				defaultValue: 'text'
			},
			error: { control: { type: 'text' } }
		},
		args: {
			type: 'text',
			label: 'Noun',
			placeholder: 'Placeholder texts are harmful',
			supportText: 'Field requirements',
			required: false
		}
	});
</script>

<script lang="ts">
	setTemplate(template);
</script>

{#snippet template({ ...args }: Args<typeof Story>)}
	<TextInput {...args} />
{/snippet}

<Story name="Primary" args={{ type: 'text' }} />

<Story name="Error" args={{ type: 'text', label: 'Noun', error: 'Error!' }} />
