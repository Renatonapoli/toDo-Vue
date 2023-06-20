<template>
  <v-flex class="logo">
    <img src="@/assets/logo.svg" alt="logo" />
  </v-flex>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "NavBar-toDO",
  // setup() {},
});
</script>

<style scope>
.logo {
  display: flex;
  justify-content: center;
  padding: 5rem 0;
  height: 200px;
  background: var(--gray-700);
}

.logo img {
  width: 7.92rem;
  height: 2.9rem;
}
</style>
