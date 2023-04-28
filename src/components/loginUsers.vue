<template>
  <v-container>
    <v-row align="center">
      <v-col cols="12" sm="8" md="6">
        <v-card>
          <v-card-title>Login</v-card-title>
          <v-card-text>
            <v-form>
              <v-text-field v-model="name" label="Name" required></v-text-field>
            </v-form>
          </v-card-text>
          <v-card-actions>
            <v-btn color="primary" @click="saveName">Save</v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  data() {
    return {
      name: "",
    };
  },
  methods: {
    saveName() {
      localStorage.setItem("name", this.name);
    },
  },
  mounted() {
    const name = localStorage.getItem("name");
    this.$emit(name);
  },
};
</script>

<style>
/* Add custom styles here */
</style>
