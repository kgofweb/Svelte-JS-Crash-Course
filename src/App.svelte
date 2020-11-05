<script>
	import Nabvar from './components/Navbar.svelte';
	import Player from './components/Player.svelte';
	import AddPlayers from './components/AddPlayers.svelte';

	// Init player
	let players = [
		{
			name: 'Jonh Doe',
			point: 53
		},
		{
			name: 'Sarra Wilson',
			point: 35
		},
		{
			name: 'Rob Smith',
			point: 41
		}
	];
	
	// Add player
	const addPlayer = (e) => {
		const newPlayer = e.detail;
		players = [...players, newPlayer];
	}

	// Remove player
	const removePlayer = (e) => {
		players = players.filter(player => player.name !== e.detail);
	}
</script>

<Nabvar/>

<div class="container">
	<AddPlayers on:addplayer={addPlayer} />
	
	{#if players.length === 0}
		<p>No players</p>
	{:else}
		{#each players as player}
			<Player name={player.name} points={player.point} on:removePlayer={removePlayer} />
		{/each}
	{/if}
</div>