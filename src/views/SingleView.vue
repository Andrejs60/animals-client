<template>
  <div class="singleAnimal"><AnimalInfo :id="id" /></div>
</template>

<script>
import AnimalInfo from "../components/animals/AnimalInfo.vue";
export default {
  name: "SingleView",
  components: { AnimalInfo },
  props: ["id"],
};
</script>

<style scoped>
.singleAnimal {
  text-align: center;
}
</style>
