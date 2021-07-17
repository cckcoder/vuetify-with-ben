<template>
  <div>
    <h1>Employee Dashboard</h1>
    <v-card>
      <v-card-title>
        Employee
        <v-spacer></v-spacer>
        <v-text-field
          v-model="search"
          append-icon="mdi-magnify"
          label="Search"
          single-line
          hide-details
        >
        </v-text-field>
      </v-card-title>
      <v-data-table
        :headers="headers"
        :items="employees"
        :items-per-page="5"
        :search="search"
        class="elevation-1"
        @click:row="selectRow"
      >
        <template v-slot:item.salary="{ item }">
          <v-chip
            :color="getColor(item.salary)"
            dark
          >
          {{ item.salary }}
          </v-chip>
        </template>
      </v-data-table>
    </v-card>

    <v-snackbar v-model="snackbar">
      You have selected: {{ selectEmployee.name }} {{ selectEmployee.title }}
      <template v-slot:action="{ attrs }">
        <v-btn
          color="pink"
          text
          v-bind="attrs"
          @click="snackbar = false"
        >
          Close
        </v-btn>
      </template>
    </v-snackbar>
  </div>
</template>

<script>
import employeeData from '@/data/employee.json'
export default {
  name: 'employee',
  data() {
    return {
      snackbar: false,
      selectEmployee: {
        name: '',
        title: ''
      },
      search: '',
      headers: [
        { 
          text: 'Id',
          value: 'id',
          sortable: false
        },
        { text: 'Emp.Name', value: 'name' },
        { text: 'Position Title', value: 'title' },
        { text: 'Salary', value: 'salary' },
      ],
      employees: employeeData
    }
  },
  methods: {
    selectRow (event) {
      this.snackbar = true
      this.selectEmployee.name = event.name
      this.selectEmployee.title = event.title
    },
    getColor (salary) {
      if(salary > 60000) return 'red'
      else if (salary > 50000) return 'orange'
      else return 'green'
    }
  },
}
</script>

<style>

</style>
