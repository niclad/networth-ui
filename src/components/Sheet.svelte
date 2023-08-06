<script lang="ts">
	import InputLabel from './InputLabel.svelte';

	interface Field {
		name: string;
		helpText?: string;
	}

	let fields: Field[] = [
		{
			name: 'cash',
			helpText: 'The money you have that you can access now with no penalty.'
		},
		{
			name: '401k'
		},
		{
			name: 'roth-ira'
		},
		{
			name: 'brokerage',
			helpText: 'Investments that are not tax advantaged.'
		},
		{
			name: 'hsa',
			helpText: 'Health Savings Account value, including amount invested.'
		},
		{
			name: 'crypto',
			helpText: 'The value of your cryptocurrency holdings.'
		},
		{
			name: 'real-estate',
			helpText: 'The value of your real estate holdings.'
		},
		{
			name: 'debt',
			helpText: 'The amount that you owe.'
		}
	];
</script>

<div class="container">
	<form>
		{#each fields as field}
			<div class="mb-3">
				<InputLabel label={field.name} helpText={field.helpText} />
				<input
					type="text"
					class="form-control"
					placeholder="0.00"
					aria-label={field.name}
					aria-describedby={field.name}
				/>
			</div>
		{/each}

		<div class="mb-3">
			<InputLabel
				label="cash"
				helpText="The money you have that you can access now with no penalty."
			/>
			<input
				type="text"
				class="form-control"
				placeholder="0.00"
				aria-label="Cash"
				aria-describedby="cash"
			/>
		</div>
	</form>
</div>

<style>
</style>
