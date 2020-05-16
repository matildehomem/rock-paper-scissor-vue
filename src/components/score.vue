<template>
  <div class="score-wrapper">
      <img src="../assets/images/logo.svg" alt="logo" />
    <div class="score">
      <p>
        score
      </p>
        <span>{{ player }}</span>
    </div>
 
  </div>
</template>
<script>
export default {
  name: "score",
  props: ['player']
};
</script>
