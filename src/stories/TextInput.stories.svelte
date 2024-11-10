<script module>
	import { defineMeta, setTemplate, type Args } from '@storybook/addon-svelte-csf';
	import { TextInput } from '$lib/components';

	const { Story } = defineMeta({
		title: 'Design System/Inputs/TextInput',
		component: TextInput,
		tags: ['autodocs'],
		argTypes: {
			value: { control: { type: 'text' } },
			placeholder: { control: { type: 'text' } },
			label: { control: { type: 'text' } },
			type: {
				control: { type: 'select' },
				options: ['text', 'password', 'email', 'number'],
				defaultValue: 'text'
			},
			required: { control: { type: 'boolean' } },
			error: { control: { type: 'text' } }
		}
	});
</script>

<script lang="ts">
	setTemplate(template);
</script>

{#snippet template({ ...args }: Args<typeof Story>)}
	<TextInput {...args} />
{/snippet}

<Story name="Primary" args={{ type: 'text', label: 'Noun', placeholder: 'Placeholder' }} />

<Story
	name="Error"
	args={{ type: 'text', label: 'Noun', placeholder: 'Placeholder', error: 'Error!' }}
/>
