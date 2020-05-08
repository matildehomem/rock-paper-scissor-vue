<template>
  <div class="score-wrapper">
      <img src="../assets/images/logo.svg" />
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
