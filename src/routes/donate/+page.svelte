<script lang="ts">
	import { Button, Group, Stack, TextInput, Textarea } from '@svelteuidev/core';
	import { pageTitle } from 'src/lib/stores';

	pageTitle.set('Donate');

	let name: string = '',
		email: string = '',
		message: string = '';

	function submit(): void {
		fetch('/api/contact', { method: 'POST', body: JSON.stringify({ name, email, message }) })
			.then((res) => res.text())
			.then((data) => console.log(data));
	}
</script>

<h1>Yes, I would like to sponsor meaningful Jewish content.</h1>
<Stack justify="left" style="width: 80%; z-index: 1;">
	<TextInput label="Name" bind:value={name} />
	<TextInput label="Email" bind:value={email} />
	<TextInput label="Message" bind:value={message} />
	<Textarea label={'Please put the following dedication in the next book ("The Baal Shem Tov\'s Practical Advice")'} bind:value={message} rows={4} />
	<Group>
		<Button color="#15b6b8" on:click={submit}>Submit</Button>
	</Group>
</Stack>
