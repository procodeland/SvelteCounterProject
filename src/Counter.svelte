<script>
	export let name;
	export let value;
	export let id;

    import { createEventDispatcher } from 'svelte'

	const dispatch = createEventDispatcher();

	
	const addPoint = () => value +=1;
	const removePoint = () => value -=1;
	const zeroPoint = () => value=0;
	const onDelete = () => {
		dispatch("removecounter", id)
	};

</script>

<main>
		<div class="card shadow1">
			<input type="text" bind:value={name}/>
			<h2>{value}</h2>
			<button class="button" on:click={addPoint}>+</button>
			<button class="button" on:click={removePoint}>-</button>
			<button class="button" on:click={zeroPoint}>0</button>
			<button class="button" on:click={onDelete}>x</button>
		</div>
</main>

<style>

    .card h2 {
        margin-right: 35px;
        margin-left: 35px;
    }

.card button {
	color: #333;
    background-color: transparent;
    outline: none;
    padding: 8px;
    border-radius: 6px;
    border-width: 4px;
    width: 50px;
    display: flex;
    font-size: 1.4rem;
    align-items: center;
    justify-content: center;
    /* font-family: 'Arial Black'; */
}
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}


	.card {
		display: flex;
		flex-direction: row;
		align-items: center;
        justify-content: center;
	}

    .card > * {
        margin-right: 10px;
    }

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>