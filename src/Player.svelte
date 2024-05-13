<script>
    export let score;
    export let winningText;
    export let won;
</script>

<style>
    .player {
        flex-grow: 1;
    }
    .plus {
        background-color: seagreen;
    }
    .minus {
        background-color: brown;
    }
    button {
        font-size: 20px;
        border-radius: 3px;
        width: 40px;
        color: white;
        font-family: monospace;
        font-weight: bold;
    }
</style>

<div class="player">
    <h2>{score}</h2>
    <button class="plus">+</button>
    <button class="minus">-</button>
    {#if won}
        <h2>{winningText}</h2>
    {/if}
</div>