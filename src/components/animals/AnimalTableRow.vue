<template>
  <tr @click="gotoAnimal(animal.id)">
    <td>{{ animal.id }}</td>
    <td>{{ animal.name }}</td>
    <td>{{ animal.class }}</td>
    <td>{{ animal.conservation_status }}</td>
    <td>{{ animal.latin_name }}</td>
  </tr>
</template>

<script>
export default {
  name: "AnimalTableRow",
  props: ["animal"],
  methods: {
    gotoAnimal(id) {
      this.$router.push(`/animals/${id}`);
    },
  },
};
</script>

<style scoped>
tr {
  cursor: pointer;
}

tr:hover {
  color: #000;
  border-left: 2px solid #0096c7;
  border-right: 2px solid #0096c7;
}
</style>
