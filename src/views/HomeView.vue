<template>
  <div class="home">
    <h1>All Animal Data</h1>
    <AnimalsTable />
  </div>
</template>

<script>
import AnimalsTable from "@/components/animals/AnimalsTable.vue";

export default {
  name: "home",
  components: { AnimalsTable },
};
</script>

<style>
.home {
  text-align: center;
}
</style>
