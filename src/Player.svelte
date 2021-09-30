<script>
    export let name;
    export let points;
	let showControls = true;

	const addPoint = () => points++;
	const removePoint = () => points--;
	const toggleControls = () => (showControls = !showControls);
    const onDelete = () => dispatch("removeplayer", name);  
</script>

<main>
    <div class="card">
        <h1> {name}
        <button class="btn btn-sm" on:click= {toggleControls}>
        {#if showControls} - {:else} +	
        {/if}</button>
        <button class="btn btn-danger btn-sm" on:click={onDelete}>x</button>
        </h1>
        <h3>Points:{points}</h3>
        {#if showControls}
        <button class="btn" on:click={addPoint}> +1</button>
        <button class="btn btn-dark" on:click={removePoint}> -1</button>
        <input type="number" bind:value={points}>
        {/if}
        
    </div>
</main>

<style>
	h1 {
		color: #204f6e;
	}
	h3 {
		margin-bottom: 30px;
	}
</style>