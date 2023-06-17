<template>
  <div class="navbar">
    <img src="@/assets/logo.svg" alt="" />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "Nav-bar",
  // setup() {},
});
</script>

<style scoped>
.navbar {
  display: flex;
  justify-content: center;
  padding: 5rem 0;
  height: 200px;
  background: var(--gray-700);
}

.navbar img {
  width: 7.92rem;
  height: 2.9rem;
}
</style>
