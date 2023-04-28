<template>
  <div>
    <p v-if="cityNames.length > 0">City Names:</p>
    <ul>
      <li v-for="cityName in cityNames" :key="cityName">{{ cityName }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      cityNames: [],
    };
  },
  mounted() {
    fetch("http://192.168.30.67:5000/json-test")
      .then((response) => response.json())
      .then((data) => {
        data.forEach((element) => {
          this.cityNames.push(element.city);
        });
      })
      .catch((error) => console.error("Error fetching data:", error));
  },
};
</script>
