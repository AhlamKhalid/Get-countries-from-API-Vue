<template>
  <div class="radio-wrapper">
    <h2 class="radio-header">Region</h2>
    <div class="radio-container">
      <input
        id="rb1"
        type="radio"
        name="region"
        value="all"
        class="radio-input"
        v-model="region"
      />
      <label for="rb1" class="radio-label"> All </label>
    </div>
    <div class="radio-container">
      <input
        id="rb2"
        type="radio"
        name="region"
        value="asia"
        class="radio-input"
        v-model="region"
      />
      <label for="rb2" class="radio-label"> Asia </label>
    </div>
    <div class="radio-container">
      <input
        id="rb3"
        type="radio"
        name="region"
        value="africa"
        class="radio-input"
        v-model="region"
      />
      <label for="rb3" class="radio-label"> Africa </label>
    </div>
    <div class="radio-container">
      <input
        id="rb4"
        type="radio"
        name="region"
        value="europe"
        class="radio-input"
        v-model="region"
      />
      <label for="rb4" class="radio-label"> Europe </label>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      region: "all"
    };
  },
  watch: {
    // Works when "region" changes
    region() {
      // emit event from child to parent
      this.$emit("change-region", this.region);
    }
  }
};
</script>

<style scoped>
/* radio */
.radio-wrapper {
  margin: 32px 0;
  display: flex;
  align-items: center;
}

.radio-header {
  font-size: 16px;
  margin-right: 32px;
}

/* No special styling for radio inputs */
.radio-input {
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
}

.radio-container {
  margin-right: 16px;
}

.radio-input {
  /* remove from document flow */
  position: absolute;
}

.radio-label {
  color: #78767a;
  font-size: 14px;
  font-weight: 700;
  /* expands its parent */
  display: inline-block;
  padding: 2px 16px;
  border-radius: 20px;
  cursor: pointer;
}

/* direct sibling */
.radio-input:checked + .radio-label {
  color: #fff;
  background-color: #0aaf6d;
}
</style>
