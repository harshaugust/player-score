<script>
	import Navbar from './Navbar.svelte';
	import Player from './Player.svelte';
	import Addplayer from './Addplayer.svelte'
	let players = [
		{
			name: "Jhon Doe",
			points: 53
		},
		{
			name: "Sam Smith",
			points: 45
		},	
		{
			name: "Sara Wilson",
			points: 34,
		}
	];
	const addplayer = (e) => {
		const newPlayer = e.detail;
		players = [...players, newPlayer];
	
	};
	const removePlayer = e => {
		players = players.filter(player => player.name !== e.detail);
	};
</script>

<main>
	<Navbar />
	<div class="container">
		<Addplayer on:addplayer = {addplayer}/>
		{#if players.length === 0}
			<p>No Player to show</p>
		{:else}
			{#each players as player}
				<Player name = {player.name} points = {player.points}
				on:removeplayer = {removePlayer	} />
			{/each}
		{/if}
	</div>
</main>
