<template>
  <div class="choices-wrapper">
    <div class="choices">
      <div
        class="choice"
        v-for="(element, index) in arrayChoice"
        :key="index"
        @click="choice"
        :id="element"
        :class="'choice-' + element"
      >
        <img :src="'/images/icon-' + element + '.svg'" class="choice-img" />
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "choices",
  props: ["arrayChoice", "choice"],
};
</script>
