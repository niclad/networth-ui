<script lang="ts">
	interface TableItem {
		name: string;
		value: number;
	}
	export let items: TableItem[];

	// Include the total in the items array if it's not already there
	// And it makes sense to do so (i.e. there are more than one items)
	if (items?.length > 1 && !items.find((item) => item.name === 'total')) {
		let total: TableItem = {
			name: 'total',
			value: items.reduce((acc, item) => acc + item.value, 0)
		};
		items.push(total);
	}
</script>

<table class="table table-borderless border-start mt-3 d-flex sticky-top">
	<tbody class="ps-2">
		{#each items as item}
			<tr class:border-top={item.name === 'total'}>
				<th class="text-end col-auto" scope="row">{item.name}</th>
				<td>${item.value}</td>
			</tr>
		{/each}
	</tbody>
</table>

<style>
	th {
		text-transform: capitalize;
	}

	.sticky-top {
		top: 4rem;
	}
</style>
