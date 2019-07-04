<template>
  <div id="app" class="container">
    <header class="header">
      <h1>Rock Paper Scissor</h1>

      <div class="score-wrapper">
        <div class="score player-score">
          <p>
            Player:
            <span>{{player}}</span>
          </p>
        </div>
        <div class="score computer-score">
          <p>
            Computer:
            <span>{{computer}}</span>
          </p>
        </div>
      </div>
    </header>
    <div class="modal" id="modal">
      <div class="results">
        <div class="computer-choice">
          <font-awesome-icon
            :icon="'hand-'+ computerChoice"
            :id="computerChoice"
            :class="'fa-hand-' + computerChoice "
            class="fas fa-10x"
          />
          <p>Computer Choose {{computerChoice}}</p>
        </div>
        <div class="result-text">
          <h1 class="text-win">{{textResult}}</h1>
        </div>
        <div class="player-choice">
          <font-awesome-icon
            :icon="'hand-'+ playerChoice"
            :id="playerChoice"
            :class="'fa-hand-' + playerChoice "
            class="fas fa-10x"
          />
          <p>You Choose {{playerChoice}}</p>
        </div>
      </div>
    </div>
    <div class="choices-wrapper">
      <h2>Make your Selection</h2>
      <div class="choices">
        <font-awesome-icon
          v-for="(element,index) in arrayChoice"
          :key="index"
          @click="choice"
          :icon="'hand-'+ element"
          :id="element"
          :class="'fa-hand-' + element "
          class="choice fas fa-5x"
        />
      </div>
    </div>
    <button id="restart" class="restart-btn" @click="restartGame">Restart Game</button>
  </div>
</template>

<script>
require("@/assets/css/app.css");

export default {
  name: "app",

  data: function() {
    return {
      player: 0,
      computer: 0,
      textResult: "",
      computerChoice: "",
      playerChoice: "",
      arrayChoice: ["rock", "paper", "scissors"]
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
      } else if (winner === "computer") {
        this.computer++;
        this.textResult = "You lose";
      } else {
        this.textResult = "It's a draw";
      }
    },
    choice: function(e) {
      this.playerChoice = e.currentTarget.id;
      this.computerChoice = this.getComputerChoice();
      const winner = this.getWinner(this.playerChoice, this.computerChoice);
      this.showWinner(winner, this.computerChoice);
    },
    restartGame: function() {
      this.player = 0;
      this.computer = 0;
    }
  }
};
</script>



