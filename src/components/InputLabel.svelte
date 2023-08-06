<script lang="ts">
	import { onMount } from 'svelte';
	import { browser } from '$app/environment';
	// import * as bootstrap from 'bootstrap';
	export let label: string;
	export let helpText: string | undefined;

	onMount(() => {
		if (browser && helpText) {
			const tooltipTriggerList = document.querySelectorAll('[data-bs-toggle="tooltip"]');
			const tooltipList = [...tooltipTriggerList].map(function (tooltipTriggerEl) {
				return new window.bootstrap.Tooltip(tooltipTriggerEl);
			});
		}
	});

	function setLabel(label: string) {
		let newLabel = label.toLowerCase().replaceAll('-', ' ');

		// Format edge cases
		switch (newLabel) {
			case 'roth ira':
				newLabel = 'Roth IRA';
				break;
			case 'real estate':
				newLabel = 'Real Estate';
				break;
			case 'hsa':
				newLabel = 'HSA';
				break;
		}

		return newLabel;
	}
</script>

<label for={label} class="form-label">
	<span class="name">{setLabel(label)}</span>
	{#if helpText}
		<i
			class="bi bi-info-circle"
			data-bs-toggle="tooltip"
			data-bs-placement="right"
			data-bs-title={helpText}
		/>
	{/if}
</label>

<style>
	.name {
		text-transform: capitalize;
	}
</style>
