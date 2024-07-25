<script lang="ts">
	import { queryParameters, ssp } from 'sveltekit-search-params';

	const urlState = queryParameters(
		{
			query: ssp.string(''),
			bool: ssp.boolean(true),
			slider: ssp.number(50)
		},
		{
			debounceHistory: 500
		}
	);
</script>

<div class="flex h-screen w-screen flex-col items-center justify-center gap-8 bg-slate-400 p-6">
	<form
		on:submit|preventDefault={() => {}}
		class="grid max-w-96 grid-cols-2 gap-4 rounded-lg bg-white p-6 shadow-md"
	>
		<p class="col-span-2">
			Change the values in the form and then use the back/forth button of the browser history to see
			the changes reflected.
		</p>
		<label for="query">Query</label>
		<input
			type="text"
			name="query"
			id="query"
			bind:value={$urlState.query}
			placeholder="Search..."
		/>
		<label for="bool">Boolean</label>
		<input type="checkbox" name="bool" id="bool" bind:checked={$urlState.bool} />
		<label for="slider">Slider</label>
		<input type="range" name="slider" id="slider" min="0" max="100" bind:value={$urlState.slider} />
	</form>
</div>
