<script>
    import AddCounter from './AddCounter.svelte'
    import Counter from './Counter.svelte'
    
	
	$: counters = [
	{
		name: 'Counter',
		value: 3,
		id: 0
	}
	];

	// $ newid değişkenini reactive hale getiriyor.
	// counter arrayi değiştiği anda newid değeri güncelleniyor
	// $ olmadan tanımlarsak ilk atanan değer neyse newid hep öyle kalıyor.
	$: newid = counters.length ? counters[counters.length -1].id +1 : 0;
	$: list = counters.map((counter)=>counter.name).join(', ');
	$: tot = counters.map(item => item.value).reduce((prev, next) => prev + next);
;

	const addCounter = (e) => {
		const newCounter = e.detail;
		console.log('all', counters)
		console.log('newCounter', newCounter)
		counters = [...counters, newCounter];
	}

	const removeCounter = (e) => {
		counters = counters.filter((counter)=> counter.id !== e.detail)
	}
</script>

<main>
	<h1>Multiple Counters</h1>
	<div class="container">
		{#if counters.length === 0}
			<p>No counter</p>
		{:else}
			{#each counters as counter, i}
			 <Counter bind:name={counter.name} bind:value={counter.value} id={counter.id} on:removecounter={removeCounter}/>
			{/each}
		{/if}
		<div class="info"><span>TITLE LIST :</span> {list}</div>
		<div class="info"><span>TOTAL :</span> {tot}</div>
		<div>
			<AddCounter on:addcounter={addCounter} id={newid}/>
		</div>
	</div>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	.info {
		margin: 20px;
		text-align: left;
	}

	.info span {
		font-weight: bold;
		font-size: 1.2rem;
		color: #003b6d
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>