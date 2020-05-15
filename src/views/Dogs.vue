<template>
  <div class="text-center">
    <h1
      class="text-3xl font-semibold text-gray-800 leading-tight tracking-tighter"
    >
      Dogs for Adoption
    </h1>
    <div class="mt-4">
      <table class="table-auto mx-auto">
        <thead>
          <tr class="bg-green-200">
            <th class="px-4 py-2 border">Name</th>
            <th class="px-4 py-2 border">Breed</th>
            <th class="px-4 py-2 border">Gender</th>
            <th class="px-4 py-2 border">Age</th>
            <th class="px-4 py-2 border">Color</th>
            <th class="px-4 py-2 border">Weight</th>
            <th class="px-4 py-2 border">Location</th>
            <th class="px-4 py-2 border">Notes</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(dog, i) in dogs" :key="i" class="hover:bg-gray-200">
            <td class="border px-4 py-2">
              <router-link :to="{ path: `pets/dogs/${i}` }">{{
                dog.name
              }}</router-link>
            </td>
            <td class="border px-4 py-2">
              {{ dog.breed }}
            </td>
            <td class="border px-4 py-2">
              {{ dog.gender }}
            </td>
            <td class="border px-4 py-2">
              {{ dog.age }}
            </td>
            <td class="border px-4 py-2">
              {{ dog.color }}
            </td>
            <td class="border px-4 py-2">
              {{ dog.weight }}
            </td>
            <td class="border px-4 py-2">
              {{ dog.location }}
            </td>
            <td class="border px-4 py-2">
              {{ dog.notes }}
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>
<script>
import { mapState } from "vuex";
export default {
  name: "Dog",
  data() {
    return {};
  },
  computed: {
    ...mapState(["dogs"])
  }
};
</script>
