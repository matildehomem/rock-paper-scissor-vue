<template>
  <div>
    <h2>Make your Selection</h2>
    <div class="choices">
      <font-awesome-icon
        icon="hand-rock"
        id="rock"
        class="choice fas fa-hand-rock fa-10x"
        @click="choice; openModal"
      />
      <font-awesome-icon
        icon="hand-paper"
        id="paper"
        class="choice fas fa-hand-paper fa-10x"
        @click="choice; openModal"
      />
      <font-awesome-icon
        icon="hand-scissors"
        id="scissors"
        class="choice fas fa-hand-scissors fa-10x"
        @click="choice; openModal"
      />
    </div>
  </div>
</template>
<script>

export default {
  name: "choices",
 
  methods: {
    openModal: function() {
      this.$refs.modal.show();
    },
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
    showWinner: function(winner, computerChoice) {
      if (winner === "player") {
        /* eslint-disable no-console */

        // Inc player score
        this.player++;
        console.log("player wins", this.player, this.computer);
        //show modal result
        this.template = `
        <h1 class="text-win">You win</h1>
        <font-awesome-icon
        icon="hand-${computerChoice}"
        id="${computerChoice}"
        class="choice fas fa-hand-${computerChoice} fa-10x"
      />
        <p>Computer Chose ${computerChoice}</p>
        `;
      } else if (winner === "computer") {
        //Inc computer score
        this.computer++;
        //show modal result

        /* eslint-disable no-console */
        console.log("computer wins", this.player, this.computer);
      } else {
        /* eslint-disable no-console */
        console.log("draw", this.player, this.computer);
      }
    },
    choice: function(e) {
      /* eslint-disable no-console */
      const playerChoice = e.currentTarget.id;
      console.log(playerChoice);
      const computerChoice = this.getComputerChoice();
      console.log(computerChoice);
      const winner = this.getWinner(playerChoice, computerChoice);
      console.log(winner);
      this.showWinner(winner, computerChoice);
      console.log(this.showModal);

      /* eslint-enable no-console */
    }
  }
};
</script>
