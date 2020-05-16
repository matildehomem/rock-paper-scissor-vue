<template>
  <div class="results">
    <div class="player-choice">
      <p>you picked</p>
      <div :id="playerChoice" :class="'choice-' + playerChoice" class="choice" >
        <div class="choice-in" :class="{winner: youWin}">
          <img
            :src="'/images/icon-' + playerChoice + '.svg'"
            class="choice-img"
            alt="player choice"
          />
        </div>
      </div>
    </div>
    <div class="results-text">
      <transition name="fade">
        <h3 class="text-win" v-if="delayed">{{ textResult }}</h3>
      </transition>
      
      <transition name="fade">
        <button @click="playAgain" class="play-again" v-if="delayed">
          play again
        </button>
      </transition>
    </div>
    <div class="computer-choice">
      <p>the house picked</p>

      <div class="empty"></div>
      <transition name="fade">
        <div
          :id="computerChoice"
          :class="'choice-' + computerChoice"
          class="choice"
          v-if="delayed"
        >
          <div class="choice-in" :class="{winner: computerWin}">
            <img
              :src="'/images/icon-' + computerChoice + '.svg'"
              class="choice-img"
              alt="computer choice"
            />
          </div>
        </div>
      </transition>
    </div>
  </div>
</template>
<script>
export default {
  name: "results",
  props: ["computerChoice", "playerChoice", "textResult", "playAgain", "youWin", "computerWin"],

  data: function() {
    return {
      delayed: false,
    };
  },
  mounted() {
    setTimeout(() => {
      this.delayed = true;
    }, 200);
  },
};
</script>
<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
  transition-delay: 0.2s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}

.text-win {
  transition: opacity 0.5s;
  transition-delay: 0.8s;
}
.play-again {
  transition: opacity 1s;
  transition-delay: 1.5s;
}
</style>
