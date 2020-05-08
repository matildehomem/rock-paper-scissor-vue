<template>
  <div class="results">
    <div class="player-choice">
      <p>you picked</p>
      <div :id="playerChoice" :class="'choice-' + playerChoice" class="choice">
        <img :src="'/images/icon-' + playerChoice + '.svg'" class="choice-img" />
      </div>
    </div>
    <div class="results-text">
      <h3 class="text-win">{{ textResult }}</h3>
      <button @click="playAgain" class="play-again">play again</button>
    </div>
    <div class="computer-choice">
      <p>the house picked</p>
      <div :id="computerChoice" :class="'choice-' + computerChoice" class="choice">
        <img :src="'/images/icon-' + computerChoice + '.svg'" class="choice-img" />
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "results",
  props: ["computerChoice", "playerChoice", "textResult", "playAgain"],
};
</script>
