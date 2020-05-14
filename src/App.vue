<template>
  <div id="app">
    <div class="container">
      <score :player="player" />
      <results
        :playAgain="playAgain"
        :computerChoice="computerChoice"
        :playerChoice="playerChoice"
        :textResult="textResult"
        :youWin="youWin"
        :computerWin="computerWin"
        v-if="played"
      />

      <choices :arrayChoice="arrayChoice" :choice="choice" v-if="!played" />
    </div>
    <rules />
  </div>
</template>

<script>
require("@/assets/css/app.scss");
import score from "./components/score.vue";
import rules from "./components/rules.vue";
import choices from "./components/choices.vue";
import results from "./components/results.vue";

export default {
  name: "app",
  components: { score, rules, choices, results },

  data: function() {
    return {
      player: 0,
      textResult: "",
      computerChoice: "",
      playerChoice: "",
      arrayChoice: ["rock", "paper", "scissors"],
      played: false,
      youWin: false,
      computerWin: false,
    };
  },

  methods: {
    getComputerChoice: function() {
      const rand = Math.random();
      if (rand < 0.34) {
        return "rock";
      } else if (rand <= 0.67) {
        return "paper";
      } else {
        return "scissors";
      }
    },
    getWinner: function(p, c) {
      if (p === c) {
        return "draw";
      } else if (p === "rock") {
        if (c === "paper") {
          return "computer";
        } else {
          return "player";
        }
      } else if (p === "paper") {
        if (c === "scissors") {
          return "computer";
        } else {
          return "player";
        }
      } else if (p === "scissors") {
        if (c === "rock") {
          return "computer";
        } else {
          return "player";
        }
      }
    },
    showWinner: function(winner) {
      if (winner === "player") {
        this.player++;
        this.textResult = "You win";
        this.youWin = true;
        this.computerWin = false;
      } else if (winner === "computer") {
        this.player == 0 ? (this.player = 0) : this.player--;
        this.textResult = "You lose";
        this.computerWin = true;
        this.youWin = false;
      } else {
        this.textResult = "It's a draw";
        this.computerWin = false;
        this.youWin = false;
      }
    },
    playAgain: function() {
      this.played = false;
    },
    choice: function(e) {
      this.playerChoice = e.currentTarget.id;
      this.computerChoice = this.getComputerChoice();
      const winner = this.getWinner(this.playerChoice, this.computerChoice);
      this.showWinner(winner, this.computerChoice);

      this.played = true;
    },
  },
};
</script>
