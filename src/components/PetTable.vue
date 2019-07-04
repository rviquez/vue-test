<template>
  <div>
    <h1>{{ species }} for adoption</h1>
    <v-data-table
      :headers="headers"
      :items="pets"
      class="elevation-1"
      dark
    >
      <template v-slot:no-data>
        <v-alert :value="true" color="error" icon="warning">
          Sorry, nothing to display here :(
        </v-alert>
      </template>
      <template v-slot:items="props">
        <td class="text-xs-left"><a @click="reRoute(props)">{{ props.item.name }}</a></td>
        <td class="text-xs-left">{{ props.item.breed }}</td>
        <td class="text-xs-left">{{ props.item.gender }}</td>
        <td class="text-xs-left">{{ props.item.age }}</td>
        <td class="text-xs-left">{{ props.item.color }}</td>
        <td class="text-xs-left">{{ props.item.weight }}</td>
        <td class="text-xs-left">{{ props.item.location }}</td>
        <td class="text-xs-left">{{ props.item.notes }}</td>
      </template>
    </v-data-table>
  </div>
</template>
<script>
export default {
  data(){
    return {
      headers: [
          { text: 'Name', value: 'name', sortable: false },
          { text: 'Breed', value: 'breed', sortable: false },
          { text: 'Gender', value: 'gender', sortable: false },
          { text: 'Age', value: 'age', sortable: false },
          { text: 'Color', value: 'color', sortable: false },
          { text: 'Weight', value: 'weight', sortable: false },
          { text: 'Location', value: 'location', sortable: false },
          { text: 'Notes', value: 'notes', sortable: false },
        ]
    }
  },
  props: {
    species: String,
    pets: Array
  },
  methods: {
    reRoute(element) {
      this.$router.push({ name: 'pet', params: { species: this.species, id: element.index } })
    }
  }
}
</script>
