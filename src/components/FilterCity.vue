<template>
  <div class="container">
    <h1>computed city search</h1>
    <div class="col">
      <input type="text" placeholder="Search city" v-model="input2" />
      <ul>
        <li v-for="(item, i) in computedList" :key="i">
          {{ item }}
        </li>
      </ul>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      input2: "",
      cityNames: [],
    };
  },
  computed: {
    computedList() {
      return this.cityNames.filter((item) => {
        return item.toLowerCase().includes(this.input2.toLowerCase());
      });
    },
  },
  mounted() {
    fetch("ir2.json")
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
<style scoped>
.container {
  margin: 0 auto;
  padding: 30px;
  max-width: 600px;
  font-family: "Avenir", Helvetica, Arial, sans-serif;
}
.col {
  width: 33%;
  height: 100%;
  float: left;
}
input {
  padding: 10px 6px;
  margin: 20px 10px 10px 0;
}
</style>
