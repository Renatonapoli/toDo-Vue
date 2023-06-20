<template>
  <v-flex>
    <Header />
    <Search />
    <lists />
  </v-flex>
</template>

<script lang="ts">
import { defineComponent } from "vue";

import Header from "./components/Header.vue";
import Search from "./components/Search.vue";
import Lists from "./components/Lists.vue";

export default defineComponent({
  name: "App",
  components: { Header, Search, Lists },
});
</script>

<style></style>
