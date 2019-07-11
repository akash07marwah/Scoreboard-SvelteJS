<script>
import Navbar from './Navbar.svelte'
import Player from './Player.svelte'
import AddPlayer from './AddPlayer.svelte'

	let Players = [
		{
			name:"John Doe",
			points:100
		},
		{
			name:"Sam Smith",
			points:100
		},
		{
			name:"Sara Wilson",
			points:100
		},
	];

	const addPlayer = (e) =>{
		const newPlayer = e.detail;
		Players = [...Players,newPlayer];
	}
	const removePlayer = (e)=>{
		Players = Players.filter(player => player.name!=e.detail);
	}
</script>

<Navbar />
<div class="container">
<AddPlayer on:addplayer={addPlayer} />
{#if Players.length === 0}
<p> No Players! </p>
{:else}
{#each Players as player}
 <Player name={player.name} points={player.points} on:removeplayer={removePlayer}/>
 {/each}
{/if} 
</div>
