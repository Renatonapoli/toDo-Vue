<template>
  <div class="logo">
    <img src="@/assets/logo.svg" alt="logo" />
  </div>
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

  @media (max-width: 768px) {
    width: 6rem;
    height: 2.9rem;
  }
}
</style>
