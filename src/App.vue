<template>
  <div>
    <TheHeader v-bind:time="time" />
    <button v-on:click="setSelectedComponent('active-goals')">
      Active goals
    </button>
    <button v-on:click="setSelectedComponent('manage-goals')">
      Manage goals
    </button>
    <!-- <ActiveGoals v-if="selectedComponent === 'active-goals'"/>
    <ManageGoals v-if="selectedComponent === 'manage-goals'"/> -->
    <keep-alive>
      <component v-bind:is="selectedComponent"></component>
    </keep-alive>
  </div>
</template>

<script>
import TheHeader from "./components/Layout/TheHeader.vue";
// import BadgeList from "./components/BadgeList.vue";
// import UserInfo from "./components/UserInfo.vue";
// import CourseGoals from "./components/CourseGoals.vue";
import ActiveGoals from "./components/ActiveGoals.vue";
import ManageGoals from "./components/ManageGoals.vue";

export default {
  components: { TheHeader, ActiveGoals, ManageGoals },
  data() {
    return {
      selectedComponent: "active-goals",
      activeUser: {
        name: "Mashu Maru",
        description: "Site owner and admin",
        role: "admin",
      },
      time: "",
      interval: 0,
    };
  },
  methods: {
    setSelectedComponent(active) {
      this.selectedComponent = active;
    },
    getTime() {
      this.time = setInterval(() => {
        var now = new Date();
        var hour = now.getHours();
        if (hour < 10) {
          hour = "0" + hour;
        }
        var minutes = now.getMinutes();
        if (minutes < 10) {
          minutes = "0" + minutes;
        }
        var seconds = now.getSeconds();
        if (seconds < 10) {
          seconds = "0" + seconds;
        }
        return (this.time = hour + " : " + minutes + " : " + seconds);
      });
    },
  },
  mounted: function() {
    this.interval = setInterval(this.getTime(), 1000);
  },
};
</script>

<style>
html {
  font-family: sans-serif;
}

body {
  margin: 0;
}

.clock {
  text-align: center;
}
</style>
