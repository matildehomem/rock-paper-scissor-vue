<template>
  <fragment>
    <button class="rules-btn" @click="rules">
      rules
    </button>
    <div v-if="modal" class="rules-modal">
      <div class="rules-wrapper">
        <button class="rules-modal-close" @click="closeRules">
          <img src="../assets/images/icon-close.svg" alt="close button" />
        </button>
        <h3>Rules</h3>
        <img src="../assets/images/image-rules.svg" alt="rules image"/>
      </div>
    </div>
  </fragment>
</template>
<script>
import { Fragment } from "vue-fragment";

export default {
  name: "rules",
  components: { Fragment },

  data() {
    return {
      modal: false,
    };
  },
  methods: {
    rules: function() {
      this.modal = true;
    },
    closeRules: function() {
      this.modal = false;
    },
  },
};
</script>
