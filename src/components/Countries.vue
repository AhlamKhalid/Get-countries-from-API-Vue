<template>
  <div>
    <div
      v-for="(country, index) in countries"
      :key="index"
      class="country-wrapper"
    >
      <div class="country-info">
        <span class="country-region">{{ country.region }} </span>
        <p class="country-name">{{ country.name }}</p>
      </div>
      <div class="country-flag">
        <img :src="country.flag" alt="country flag" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  // props sent from parent to child
  props: ["countries"]
};
</script>

<style scoped>
/* country */
.country-wrapper {
  display: flex;
  justify-content: space-between;
  background-color: #350c50;
  border-radius: 5px;
  margin-bottom: 16px;
}

.country-info {
  padding: 24px 0 24px 24px;
}

.country-region {
  text-transform: uppercase;
  font-size: 14px;
  font-weight: 700;
  background-color: #220039;
  border-radius: 20px;
  padding: 2px 16px;
}

.country-name {
  font-size: 18px;
  margin-top: 6px;
}

.country-flag {
  width: 86px;
  background-color: #3f0e5f;
  border-top-right-radius: 5px;
  border-bottom-right-radius: 5px;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 24px;
}
</style>
