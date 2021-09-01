<template>
  <div class="container">
    <h1 class="header">
      <a href="https://restcountries.eu/" target="_blank">Countries API</a>
    </h1>
    <!-- region radio -->
    <Region @change-region="changeRegion" />
    <!-- countries or loading -->
    <div v-if="isLoading" class="loading-circle"></div>
    <Countries v-else :countries="countries" />
  </div>
</template>

<script>
// components
import Countries from "@/components/Countries";
import Region from "@/components/Region";
// axios
import axios from "axios";

export default {
  components: {
    Countries,
    Region
  },
  data() {
    return {
      apiUrl: "https://restcountries.eu/rest/v2/all",
      countries: [],
      isLoading: true
    };
  },
  created() {
    this.getCountries();
  },
  methods: {
    async getCountries() {
      try {
        const response = await axios.get(this.apiUrl);
        this.countries = response.data;
      } catch (error) {
        console.log(error);
      }

      this.isLoading = false;
    },
    changeRegion(region) {
      if (region === "all") {
        this.apiUrl = "https://restcountries.eu/rest/v2/all";
      } else {
        this.apiUrl = `https://restcountries.eu/rest/v2/region/${region}`;
      }

      this.isLoading = true;
      this.getCountries();
    }
  }
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font-family: "Open Sans", sans-serif;
  background-color: #220039;
  color: #fff;
}

a {
  text-decoration: none;
  color: inherit;
}

img {
  max-width: 100%;
}

.container {
  max-width: 1000px;
  margin: 0 auto;
  padding: 0 24px;
}

/* header */
.header {
  margin-top: 72px;
  font-size: 24px;
  position: relative;
  padding-top: 16px;
}

.header::before {
  content: "";
  width: 32px;
  height: 8px;
  background-color: #0aaf6d;
  border-radius: 5px;
  position: absolute;
  left: 0;
  top: 0;
}

.loading-circle {
  width: 32px;
  height: 32px;
  margin: 20px auto;
  border: 4px rgba(255, 255, 255, 0.25) solid;
  border-top: 4px #fff solid;
  border-radius: 50%;
  animation: spin 0.6s infinite linear;
}

@keyframes spin {
  from {
    transform: rotate(0deg);
  }

  to {
    transform: rotate(359deg);
  }
}
</style>
