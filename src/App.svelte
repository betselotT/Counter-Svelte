<script>
	import Player from './Player.svelte';
	let redScore = 10;
	let blueScore = 10;
	$: blueWon = redScore <= 0;
	$: redWon = blueScore <= 0;
	$: gameOver = blueWon || redWon; 

	function updateBlueScore(e) {
		const updateScore = e.detail;
		blueScore += updateScore;
	}

	function updateRedScore(e) {
		const updateScore = e.detail;
		redScore += updateScore;
	}
	
	function newGame() {
		redScore = 10;
		blueScore = 10;
	}
</script>

<style>
	main {
		width: 80%;
		padding: 20px;
		border: solid gray 1px;
		margin: 0 auto;
		background-color: wheat;
		margin: 10vh auto;
	}
	#controls-container {
		display: flex;
	}
	button {
		display: block;
		width: 100%;
		margin-top: 20px;
		border: solid salmon 1px;
		background-color: sandybrown;
		color: rgb(61, 56, 56);
		font-size: 20px;
		border-radius: 3px;
	}
	button:hover {
		cursor: pointer;
	}
</style>

<main>
	<h1>Counters</h1>
	<div id="controls-container">
		<Player on:points={updateBlueScore} {gameOver} fontColor="#0000AA" won={blueWon} winningText="Blue Wins!" score={blueScore} />
		<Player on:points={updateRedScore} {gameOver} fontColor="#AA0000" won={redWon} winningText="Red Wins!" score={redScore} />
	</div>
	<button on:click={newGame}>Start Game</button>
</main>