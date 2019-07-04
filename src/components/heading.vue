<template>
  <header class="header">
    <h1>Rock Paper Scissor</h1>

    <button id="restart" class="restart-btn">Restart Game</button>

    <div class="score-wrapper">
      <div class="score player-score">
        <p>Player:
        <span>{{player}}</span></p>
      </div>
      <div class="score computer-score">
        <p>Computer: 
         <span>{{computer}}</span></p>
      </div>
    </div>
  </header>
</template>


<script>
export default {
  data() {
    return {
      player: 0
    };
  }
};
</script>
