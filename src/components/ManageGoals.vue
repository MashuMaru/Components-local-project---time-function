<template>
  <div>
    <h2>Manage Goals</h2>
    <input type="text" ref="goal" />
    <button v-on:click="setGoal">Set Goal</button>
    <teleport to="body">
      <error-alert v-if="inputIsInvalid">
        <h2>Invalid input!</h2>
        <p>You need to write at least a few characters...</p>
        <button v-on:click="errorConfirmed">Gotcha!</button>
      </error-alert>
    </teleport>
  </div>
</template>

<script>
import ErrorAlert from "./ErrorAlert.vue";

export default {
  components: { ErrorAlert },
  data: function() {
    return {
      inputIsInvalid: false,
    };
  },
  methods: {
    setGoal() {
      const enteredValue = this.$refs.goal.value;
      if (enteredValue === "") {
        this.inputIsInvalid = true;
      }
    },
    errorConfirmed() {
      this.inputIsInvalid = false;
    },
  },
};
</script>

<style></style>
