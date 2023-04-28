<template>
  <v-container fluid>
    <v-row>
      <v-col cols="auto">
        <v-tabs v-model="activeTab" color="blue" vertical>
          <v-tab v-for="tab in tabs" :key="tab" @click="changeTab(tab)">
            {{ tab }}
          </v-tab>
        </v-tabs>
      </v-col>
      <v-col cols="10">
        <v-card>
          <v-card-text>
            <h1>{{ activeTab }}</h1>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      activeTab: "Dashboard",
      tabs: ["Dashboard", "Todos", "Weather", "Profile"],
    };
  },
  methods: {
    changeTab(tab) {
      this.activeTab = tab;
    },
  },
};
</script>

<style scoped>
.v-tabs__wrapper {
  height: 100%;
}

.v-tabs__container {
  height: 100%;
}

.v-tabs__content {
  height: 100%;
}

.v-tabs__item {
  height: auto !important;
  padding: 24px;
}

.v-tabs__item--active {
  background-color: #e0e0e0;
}
</style>
