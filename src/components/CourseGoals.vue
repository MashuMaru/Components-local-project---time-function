<template>
  <ul>
    <li v-for="goal in goals" v-bind:key="goal">
        <slot v-bind:item="goal" another-prop="..."></slot>
    </li>
  </ul>
</template>

<script>
export default {
  data: function() {
    return {
      goals: ["Finish the course", "Learn Vue"],
    };
  },
};
</script>
