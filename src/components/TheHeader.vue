<template>
  <header>
    <h1>More on Vue Components</h1>
    <h3>{{time}}</h3>
  </header>
</template>

<script>
export default {
  props: ["time"],
}
</script>

<style>
  header {
    width: 100%;
    height: 100px;
    /* display: flex; */
    text-align: center;
    align-items: center;
    background-color: #14005e;
  }

  header h1 {
    color: white;
    margin: 0;
    padding-top: 15px;
    padding-bottom: 10px;
  }

  h3 {
    color: white;
    margin: 0;
  }
</style>