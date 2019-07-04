<template>
  <div class="home-view-container">
    <h1>Adopt a new best firend!</h1>
    {{ getAllCats.length }}
    {{ animalsCount }}
    <v-btn @click="togglePetForm" color="info">Add New Pet</v-btn>
    <v-form @submit.prevent="handleSubmit" v-if="showPetForm">
      <v-container>
        <v-layout>
          <v-flex
            xs12
            md3
          >
            <v-text-field
              v-model="formData.name"
              label="Pet's name"
            ></v-text-field>
          </v-flex>

          <v-flex
            xs12
            md3
          >
            <v-select
              v-model="formData.species"
              :items="['cats', 'dogs']"
              label="Species"
            ></v-select>
          </v-flex>

          <v-flex
            xs12
            md3
          >
            <v-text-field
              v-model="formData.age"
              label="Pet's Age"
              type="number"
              suffix="years"
            ></v-text-field>
          </v-flex>
          <v-flex
            xs12
            md3
          >
            <v-btn
              type="submit"
              color="success"
            >
              Add
            </v-btn>
            <v-btn
              color="error"
            >
              Reset
            </v-btn>
          </v-flex>
        </v-layout>
      </v-container>
    </v-form>
  </div>
</template>
<script>
import { mapActions, mapGetters } from 'vuex'

export default {
  name: 'home',
  data() {
    return {
      showPetForm: false,
      formData: {
        name: '',
        age: 0,
        species: null
      }
    }
  },
  computed: {
    ...mapGetters([
      'animalsCount',
      'getAllCats'
    ])
  },
  methods: {
    ...mapActions([
      'addPet'
    ]),
    togglePetForm() {
      this.showPetForm = !this.showPetForm;
    },
    handleSubmit() {
      const { species, age, name } = this.formData
      const payload = {
        species,
        pet: {
          name,
          age
        }
      }
      this.addPet(payload)

      //reset form
      this.formData = {
        name: '',
        age: 0,
        species: null
      }
    }
  }
}
</script>
