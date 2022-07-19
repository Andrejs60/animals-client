<template>
  <h1>Animal Details</h1>
  <div v-if="animal" class="animal-details">
    <h3>Name: {{ animal.name }}</h3>
    <h3>ID: {{ animal.id }}</h3>
    <h3>Class: {{ animal.class }}</h3>
    <h3>Conservation Status: {{ animal.conservation_status }}</h3>
    <h3>Latin Name: {{ animal.latin_name }}</h3>
  </div>
  <p v-else-if="!animal && !error">Loading animal data...</p>
  <p class="error" v-if="error">{{ error }}</p>
</template>

<script>
import axios from "axios";

export default {
  name: "AnimalInfo",
  props: ["id"],
  data() {
    return {
      animal: null,
      error: null,
    };
  },
  created() {
    this.fetchAnimal();
  },
  methods: {
    async fetchAnimal() {
      try {
        const { data } = await axios.get(
          `http://127.0.0.1:8000/api/animals/get/${this.id}`
        );
        this.animal = data.animal;
      } catch (error) {
        console.error(error);
        this.error = "Failed fetching animal data.";
      }
    },
  },
};
</script>

<style></style>
