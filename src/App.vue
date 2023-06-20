<template>
  <div>
    <Header />
    <main class="container">
      <Lists />
    </main>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";

import Header from "./components/Header.vue";
import Lists from "./components/Lists.vue";

import "../src/global.css";

export default defineComponent({
  name: "App",
  components: { Header, Lists },
});
</script>

<style scope>
.container {
  display: flex;
  justify-content: center;

  @media (max-width: 768px) {
    padding-inline: 0.5rem;
  }
}
</style>
