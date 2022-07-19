<template>
  <div class="table-box" v-if="animals.length !== 0">
    <table>
      <tr>
        <th>ID</th>
        <th>Name</th>
        <th>Class</th>
        <th>Conservation Status</th>
        <th>Latin Name</th>
      </tr>
      <AnimalTableRow
        v-for="animal in animals"
        :animal="animal"
        :key="animal.id"
      />
    </table>
  </div>

  <p v-else-if="animals.length === 0 && !error">Loading animal data...</p>
  <p class="error" v-if="error">{{ error }}</p>
</template>

<script>
import axios from "axios";
import AnimalTableRow from "./AnimalTableRow.vue";

export default {
  name: "AnimalsTable",
  components: { AnimalTableRow },
  data() {
    return {
      animals: [],
      error: null,
    };
  },
  created() {
    this.fetchAnimals();
  },
  methods: {
    async fetchAnimals() {
      try {
        const { data } = await axios.get(
          "http://127.0.0.1:8000/api/animals/list"
        );
        this.animals = data.animals;
      } catch (error) {
        console.error(error);
        this.error = "Failed fetching animal data.";
      }
    },
  },
};
</script>

<style>
.error {
  color: red;
  font-weight: bold;
  font-size: 24px;
}

.table-box {
  display: table;
  padding: 16px;
  width: 1200px;
  margin: 0 auto;
  background: #caf0f8;
  border-radius: 8px;
}

table {
  width: 100%;

  border-collapse: collapse;
  box-sizing: border-box;
}

th {
  background: #90e0ef;
}

tr {
  background: #ade8f4;
  border: 2px solid transparent;
}

th,
td {
  padding: 24px;
}

tr:first-child {
  border-top: none;
}
/* tr:last-child {
  border-bottom: none;
} */

tr:nth-child(even) {
  background: #caf0f8;
}

@media (max-width: 1300px) {
  .table-box {
    width: 800px;
  }
}

@media (max-width: 900px) {
  .table-box {
    width: 90%;
    overflow-x: auto;
  }
}
</style>
