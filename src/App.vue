<template>
  <v-flex>
    <Header />
    <main class="container">
      <Lists />
    </main>
  </v-flex>
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
  width: 100%;
}
</style>
