<template>
  <div>
    <TheHeader />
    <BadgeList />
    <UserInfo
      :full-name="activeUser.name"
      :info-text="activeUser.description"
      :role="activeUser.role"
    />
    <p>
      <span>{{ hour }} </span>
    </p>
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
      hour: "",
      // minutes: minutes,
    };
  },
  methods: {
    getHours() {
      this.hour = setInterval(() => {
        var now = new Date();
        var hour = now.getHours();
        var minutes = now.getMinutes();
        var seconds = now.getSeconds();
        return (this.hour = hour + " : " + minutes + " : " + seconds);
      });
      // var now = new Date();
      // var hour = now.getHours();
      // var minutes = now.getMinutes();
      // var seconds = now.getSeconds();
      // return (this.hour = hour + " : " + minutes + " : " + seconds);
    },
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
