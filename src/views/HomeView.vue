<template>
  <div>
    <NavBar />
    <Search />
    <Lists />
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import NavBar from "../components/Navbar.vue";
import Search from "../components/Search.vue";
import Lists from "../components/Lists.vue";

export default defineComponent({
  components: { NavBar, Search, Lists },
  name: "Home-Lists",
  // setup() {},
});
</script>
