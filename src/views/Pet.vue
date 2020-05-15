<template>
  <div class="text-center">
    <h1 class="text-3xl font-mono text-gray-800">
      {{ animal.name }} ({{ $route.params.species }})
    </h1>
    <p class="text-2xl font-mono text-gray-800">
      Age: {{ animal.age }} yours old
    </p>
    <p class="text-2xl font-mono text-gray-800">Breed: {{ animal.breed }}</p>
  </div>
</template>
<script>
import { mapState } from "vuex";
export default {
  name: "Pet",
  data() {
    return {
      animal: {}
    };
  },
  computed: {
    ...mapState(["cats", "dogs"])
  },
  mounted() {
    const animal = this[this.$route.params.species][this.$route.params.id];
    this.animal = animal;
  }
};
</script>
