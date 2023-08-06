<script lang="ts">
	import Header from '../components/Header.svelte';
	import Footer from '../components/Footer.svelte';
	import Controls from '../components/Controls.svelte';
	import RunningTotal from '../components/RunningTotal.svelte';

	/**
	 * Cash
	 * 401k
	 * Roth IRA
	 * Brokerage
	 * HSA
	 * Crypto
	 * Real Estate
	 * Debt
	 * Other
	 */

	let fields: string[] = [
		'cash',
		'401k',
		'roth ira',
		'brokerage',
		'hsa',
		'crypto',
		'real estate',
		'debt',
		'other'
	];

	interface TableItem {
		name: string;
		value: number;
	}

	let items: TableItem[] = [
		{
			name: 'cash',
			value: 1234.56
		},
		{
			name: 'brokerage',
			value: 6789.1
		}
	];
</script>

<!-- nav bar -->

<!-- header -->
<Header />

<!-- controls -->
<Controls />

<!-- content -->
<div class="container">
	<div class="row">
		<div class="col" />
		<div class="col-6">
			<slot />
		</div>
		<div class="col">
			<RunningTotal {items} />
		</div>
	</div>
</div>

<!-- footer -->
<Footer />

<style>
</style>
