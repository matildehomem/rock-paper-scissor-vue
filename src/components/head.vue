<template>
 <div class="header">
        <h1>Rock Paper Scissor</h1>

        <button id="restart" class="restart-btn">Restart Game</button>

        <div id="score" class="score">
          <p>Player: {{player}}</p>
          <p>Computer: {{computer}}</p>
        </div>

      </div>
</template>

<script>

export default {
    data(){
        return {player: 0, computer: 0};
    }
}
</script>

<style>
.restart-btn {
  display: none;
  background: var(--light-color);
  color: #333;
  padding: 0.4rem 1.3rem;
  font-size: 1rem;
  cursor: pointer;
  outline: none;
  border: none;
  margin-bottom: 1rem;
}

.restart-btn:hover {
  background: var(--primary-color);
  color: #fff;
}

.header {
  text-align: center;
  margin: 1rem 0;
}

.header h1 {
  margin-bottom: 1rem;
}

.score {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  font-size: 1.2rem;
  color: #fff;
}

.score p:first-child {
  background: var(--primary-color);
}

.score p:last-child {
  background: var(--dark-color);
}

</style>