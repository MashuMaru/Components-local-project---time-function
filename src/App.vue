<template>
  <div>
    <p>
      <span>{{ time }} </span>
    </p>
    <TheHeader />
    <BadgeList />
    <UserInfo
      :full-name="activeUser.name"
      :info-text="activeUser.description"
      :role="activeUser.role"
    />
  </div>
</template>

<script>
import TheHeader from "./components/TheHeader";
import BadgeList from "./components/BadgeList";
import UserInfo from "./components/UserInfo";

export default {
  components: { TheHeader, BadgeList, UserInfo },
  data() {
    return {
      activeUser: {
        name: "Maximilian Schwarzmüller",
        description: "Site owner and admin",
        role: "admin",
      },
      time: "",
      interval: 0,
      // minutes: minutes,
    };
  },
  methods: {
    getHours() {
      this.time = setInterval(() => {
        var now = new Date();
        //hours
        var hour = now.getHours();
        if (hour < 10) {
          hour = "0" + hour;
        }
        //minutes
        var minutes = now.getMinutes();
        if (minutes < 10) {
          minutes = "0" + minutes;
        }
        //seconds
        var seconds = now.getSeconds();
        if (seconds < 10) {
          seconds = "0" + seconds;
        }
        return (this.time = hour + " : " + minutes + " : " + seconds);
      });
      // var now = new Date();
      // var hour = now.getHours();
      // var minutes = now.getMinutes();
      // var seconds = now.getSeconds();
      // return (this.hour = hour + " : " + minutes + " : " + seconds);
    },
  },
  mounted: function() {
    this.interval = setInterval(this.getHours(), 1000);
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
</style>
