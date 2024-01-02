<script lang="ts">
	import { Button, Group, Stack, TextInput } from '@svelteuidev/core';
	import { pageTitle } from 'src/lib/stores';

	pageTitle.set('Contact Info');

	let name: string = '',
		email: string = '',
		message: string = '';
</script>

<h1>We love hearing from our readers.</h1>
<Stack justify="left" style="width: 80%; z-index: 1;">
	<TextInput label="Name" bind:value={name} />
	<TextInput label="Email" bind:value={email} />
	<TextInput label="Message" bind:value={message} />
	<Group>
		<Button color="#15b6b8">Submit</Button>
	</Group>
</Stack>
