<script module>
	import { defineMeta, setTemplate, type Args } from '@storybook/addon-svelte-csf';
	import { Icon } from '$lib/components/index';
	import IconComponent from '$lib/icons/IconComponent.svelte';

	const { Story } = defineMeta({
		title: 'Atoms/Icon',
		component: Icon,
		tags: ['autodocs'],
		argTypes: {
			spin: {
				control: { type: 'boolean' },
				defaultValue: false
			}
		}
	});
</script>

<script lang="ts">
	setTemplate(template);
</script>

{#snippet template({ ...args }: Args<typeof Story>)}
	<Icon {...args}><IconComponent /></Icon>
{/snippet}

<!-- It's not recommended to have more than one primary button per screen/area -->
<Story name="Spin" args={{ spin: false }} />

<!-- Consider using a secondary button for more subtle actions -->
<Story name="Secondary" args={{ spin: true }} />
