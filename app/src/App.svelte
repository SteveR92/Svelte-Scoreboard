<script>
	import Navbar from './Navbar.svelte'
	import Player from './Player.svelte'
	import AddPlayer from './AddPlayer.svelte'


	let players = [
		{
			name: "John",
			points: 53
		},
		{
			name: "Simon",
			points: 23
		},
		{
			name: "Dan",
			points: 83
		},
	]

	const addPlayer = e => {
		console.log(e.detail)
		const newPlayer =  e.detail
		players = [...players, newPlayer]
	}

	const removePlayer = e => {
		players = players.filter(player => player.name !== e.detail)
	}
</script>

<main>
<Navbar />
	<div class="container">
	<AddPlayer on:addplayer={addPlayer} />
		{#if players.length === 0}
			<p>No Players</p>
		{:else}
			{#each players as player}
				<Player 
					name={player.name} 
					points={player.points} 
					on:removeplayer={removePlayer}
				/>
			{/each}
		{/if}
	</div>
</main>
 
