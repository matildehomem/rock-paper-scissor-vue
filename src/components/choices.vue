<template>
  <div class="choices-wrapper">
    <div class="choices">
      <a
        class="choice"
        v-for="(element, index) in arrayChoice"
        :key="index"
        @click="choice"
        :id="element"
        :class="'choice-' + element"
      >
      <div class="choice-in">
        <img :src="'/images/icon-' + element + '.svg'" class="choice-img" alt="choice element"/>

      </div>

      </a>
    </div>
  </div>
</template>
<script>
export default {
  name: "choices",
  props: ["arrayChoice", "choice"],
};
</script>
