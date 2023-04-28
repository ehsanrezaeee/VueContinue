<template>
  <div class="wrapper">
    <nav>
      <ul>
        <li
          @click="activeTab = 'Dashboard'"
          :class="{ active: activeTab === 'Dashboard' }"
        >
          Dashboard
        </li>
        <li
          @click="activeTab = 'Todos'"
          :class="{ active: activeTab === 'Todos' }"
        >
          Todos
        </li>
        <li
          @click="activeTab = 'Weather'"
          :class="{ active: activeTab === 'Weather' }"
        >
          Weather
        </li>
        <li
          @click="activeTab = 'Profile'"
          :class="{ active: activeTab === 'Profile' }"
        >
          Profile
        </li>
      </ul>
    </nav>

    <div class="content">
      <div v-if="activeTab === 'Dashboard'">
        <FilterCity />
        <!-- Your dashboard content here -->
      </div>

      <div v-if="activeTab === 'Todos'">
        <TodoList2 />
        <!-- Your todos content here -->
      </div>

      <div v-if="activeTab === 'Weather'">
        <weatherApi />
        <!-- Your weather content here -->
      </div>

      <div v-if="activeTab === 'Profile'">
        <h1>Profile</h1>
        <!-- Your profile content here -->
      </div>
    </div>
  </div>
</template>

<script>
import TodoList2 from "./TodoList2.vue";
import weatherApi from "./weatherApi.vue";
import FilterCity from "./FilterCity.vue";
export default {
  components: {
    weatherApi,
    // solveProblem,
    FilterCity,
    TodoList2,
  },
  data() {
    return {
      activeTab: "Dashboard",
    };
  },
};
</script>

<style>
.wrapper {
  display: flex;
  flex-direction: row;
  height: 100vh;
}

nav {
  background-color: #333;
  color: #fff;
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
  align-items: flex-start;
  padding: 10px;
}

nav ul {
  display: flex;
  flex-direction: column;
  list-style: none;
  margin: 0;
}

nav li {
  cursor: pointer;
  font-weight: bold;
  padding: 10px;
  transition: background-color 0.2s ease-in-out;
}

nav li.active {
  background-color: #4caf50;
}

.content {
  padding: 20px;
}
</style>
