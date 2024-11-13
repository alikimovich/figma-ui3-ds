<script module>
	import { defineMeta, setTemplate, type Args } from '@storybook/addon-svelte-csf';

	import { Icon } from '$lib/components/index.js';
	import { IconComponent } from '$lib/icons/index.js';

	const { Story } = defineMeta({
		title: 'Design System/Atoms/Icon',
		component: Icon,
		tags: ['autodocs'],
		argTypes: {
			iconName: {
				defaultValue: IconComponent
			},
			iconChar: {
				control: { type: 'text' }
			},
			spin: {
				control: { type: 'boolean' },
				defaultValue: false
			},
			color: {
				control: { type: 'color' }
			}
		}
	});
</script>

<script lang="ts">
	setTemplate(template);
</script>

{#snippet template({ ...args }: Args<typeof Story>)}
	<Icon iconName={IconComponent} {...args} />
{/snippet}

<Story name="Static" args={{ spin: false }} />

<Story name="Spin" args={{ spin: true }} />
