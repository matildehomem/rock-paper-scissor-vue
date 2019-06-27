<template>
  <div class="choices">
    <h2>Make your Selection</h2>
    <i id="rock" class="choice fas fa-hand-rock fa-10x"></i>
    <i id="paper" class="choice fas fa-hand-paper fa-10x"></i>
    <i id="scissors" class="choice fas fa-hand-scissors fa-10x"></i>
  </div>
</template>
<style>
.choices {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 2rem;
  margin-top: 3rem;
  text-align: center;
}

.choice {
  cursor: pointer;
}

.choice:hover {
  color: var(--primary-color);
}

.text-win {
  color: var(--win-color);
}

.text-lose {
  color: var(--lose-color);
}
</style>
