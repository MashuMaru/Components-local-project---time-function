<template>
  <section>
    <base-card>
      <template v-slot:header>
        <h3 class="fullname">{{ fullName }}</h3>
        <BaseBadge :type="role" :caption="role.toUpperCase()" />
      </template>
      <template v-slot:default>
        <p>{{ infoText }}</p>
      </template>
    </base-card>
  </section>
</template>

<script>
import BaseBadge from "./BaseBadge";
export default {
  components: { BaseBadge },
  props: ["fullName", "infoText", "role"],
};
</script>
