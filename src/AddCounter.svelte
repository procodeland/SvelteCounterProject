<script>
    import { createEventDispatcher } from 'svelte'

const dispatch = createEventDispatcher();
export let id;

let counter = {
    name: `Counter ${id}`,
    value: 0,
    id: id
}

function addNewCounter(e){
    e.preventDefault();
    dispatch("addcounter",counter);
    counter ={
        name: `Counter ${id+1}`,
        value: 0,
        id: id+1
    }
}
</script>

<button class="add-btn"on:click={addNewCounter}>New Counter</button>