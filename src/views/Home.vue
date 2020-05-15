<template>
  <div class="text-center">
    <h1 class="text-4xl font-mono text-gray-700 leading-tight tracking-normal">
      Adopt a New Best Friend
    </h1>
    <p>{{ getAllCats.length }} {{ animalCount }}</p>
    <div class="relative mt-8">
      <button
        @click="toggleForm"
        type="button"
        class="border px-3 py-2 rounded bg-blue-600 text-sm font-mono text-white focus:outline-none hover:bg-blue-500 active:bg-blue-700"
      >
        Add New Pet
      </button>
      <div class="mt-8 flex justify-center">
        <form class="w-1/2" v-if="formShow" @submit.prevent="handleSubmit">
          <div class="">
            <label for="pname" class="block text-sm font-mono text-gray-700"
              >Pet`s Name:</label
            >
            <input
              type="text"
              name=""
              class="border border-gray-500 w-64 px-3 py-2 rounded focus:outline-none focus:border-gray-400"
              placeholder="Enter a pet name"
              id="pname"
              v-model="formData.name"
            />
          </div>
          <div class="">
            <label for="pname" class="block text-sm font-mono text-gray-700"
              >Species:</label
            >
            <select
              class="border border-gray-500 w-64 px-3 py-2 rounded focus:outline-none focus:border-gray-400"
              v-model="formData.species"
            >
              <option value="cats">Cats</option>
              <option value="dogs">Dogs</option>
            </select>
          </div>
          <div class="">
            <label for="age" class="block text-sm font-mono text-gray-700"
              >Pet`s Age:</label
            >
            <input
              type="number"
              name=""
              class="border border-gray-500 w-64 px-3 py-2 rounded focus:outline-none focus:border-gray-400"
              id="age"
              v-model="formData.age"
            />
          </div>
          <div class="mt-3">
            <button
              type="submit"
              class="border px-3 py-2 rounded bg-blue-600 text-sm font-mono text-white focus:outline-none hover:bg-blue-500 active:bg-blue-700"
            >
              Submit
            </button>
            <button
              type="button"
              class="border px-3 py-2 rounded bg-red-600 text-sm font-mono text-white focus:outline-none hover:bg-red-500 active:bg-red-700"
              @click="formShow = false"
            >
              Cancel
            </button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import { mapActions, mapGetters } from "vuex";
export default {
  name: "Home",
  data() {
    return {
      formShow: false,
      formData: {
        name: "",
        species: null,
        age: 0
      }
    };
  },
  computed: {
    ...mapGetters(["animalCount", "getAllCats"])
  },
  methods: {
    ...mapActions(["addPet"]),
    toggleForm() {
      this.formShow = !this.formShow;
    },
    handleSubmit() {
      const { species, name, age } = this.formData;
      const payload = {
        species,
        pet: {
          name,
          age
        }
      };
      this.addPet(payload);
      // Reset form
      this.formData = {
        name: "",
        species: null,
        age: 0
      };
    }
  },
  components: {}
};
</script>
