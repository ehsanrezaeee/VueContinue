<template>
  <div>
    <label for="latitude">Latitude:</label>
    <input id="latitude" type="number" v-model="latitude" />
    <br />
    <label for="longitude">Longitude:</label>
    <input id="longitude" type="number" v-model="longitude" />
    <br />
    <p>Current Temperature: {{ currentTemperature }}°C</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      latitude: 38.08,
      longitude: 46.29,
      currentTemperature: null,
    };
  },
  watch: {
    latitude: function () {
      this.fetchCurrentTemperature();
    },
    longitude: function () {
      this.fetchCurrentTemperature();
    },
  },
  mounted() {
    this.fetchCurrentTemperature();
  },
  methods: {
    fetchCurrentTemperature() {
      const url = `https://api.open-meteo.com/v1/forecast?latitude=${this.latitude}&longitude=${this.longitude}&current_weather=true`;
      fetch(url)
        .then((response) => response.json())
        .then(
          (data) => (this.currentTemperature = data.current_weather.temperature)
        )
        .catch((error) => console.error("Error fetching data:", error));
    },
  },
};
</script>
