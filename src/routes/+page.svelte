<script lang="ts">
	//import type { PageData } from './$types';
  import { superForm } from 'sveltekit-superforms/client';
  import SuperDebug from 'sveltekit-superforms/client/SuperDebug.svelte';

  export let data; // : PageData

  const { form, errors, constraints } = superForm(data.form);
</script>

<SuperDebug data={$form} />

<form method="POST">
	<label for="name">Name</label>
	<input
		type="text"
		name="name"
		data-invalid={$errors.name}
		bind:value={$form.name}
		{...$constraints.name}
	/>
	{#if $errors.name}<span class="invalid">{$errors.name}</span>{/if}

	<label for="email">E-mail</label>
	<input
		type="email"
		name="email"
		data-invalid={$errors.email}
		bind:value={$form.email}
		{...$constraints.email}
	/>
	{#if $errors.email}<span class="invalid">{$errors.email}</span>{/if}

	<div><button>Submit</button></div>
</form>

<div style="margin-top:2rem;">
	<a target="_blank" href="https://superforms.vercel.app/get-started">Tutorial for this example here</a>
</div>

<style>
	.invalid {
		color: red;
	}
</style>
