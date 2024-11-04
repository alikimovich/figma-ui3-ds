<script module>
	import { defineMeta, setTemplate, type Args } from '@storybook/addon-svelte-csf';
	import Button from './Button.svelte';
	import { fn } from '@storybook/test';

	// More on how to set up stories at: https://storybook.js.org/docs/writing-stories
	const { Story } = defineMeta({
		title: 'Example/Button',
		component: Button,
		tags: ['autodocs'],
		argTypes: {
			size: {
				control: { type: 'select' },
				options: ['small', 'medium', 'large']
			}
		},
		args: {
			label: 'Button',
			primary: false,
			size: 'medium',
			onClick: fn(),
			children: 'Hey hey!'
		}
	});
</script>

<script lang="ts">
	setTemplate(template);
</script>

{#snippet template({ children, ...args }: Args<typeof Story>)}
	<Button {...args}>{children}</Button>
{/snippet}

<!-- More on writing stories with args: https://storybook.js.org/docs/writing-stories/args -->
<Story name="Primary" args={{ primary: true, label: 'Button' }} />

<Story name="Secondary" args={{ label: 'Button' }} />

<Story name="Large" args={{ size: 'large', label: 'Button' }} />

<Story name="Small" args={{ size: 'small', label: 'Button' }} />
