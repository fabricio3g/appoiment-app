<template>
<div class='d-flex justify-center flex-column'>
  <div class='mx-auto mt-5'>
  <h1 class="mb-5">{{ title }}</h1>
  <AppointmentsList v-if="appointments" @remove="removeItem" @edit="editItem"  :appointments="appointments"/>
  </div>
  </div>
</template>

<script>
import axios from 'axios'
import AppointmentsList from './components/AppointmentsList'
import _ from 'lodash'
export default {
  name: "App",
  data: () => {
    return {
      title: "Appoiment List",
      appointments: null,
      aptIndex: 0
    };
  },
  async mounted() {
    let data = await (axios.get('https://gist.githubusercontent.com/planetoftheweb/46426d47f21f2c9245bbe23f0fb834b5/raw/afae0adf97472893288ac5cde69e7bbb770793ed/appointments.json')
    .then(data => data.data)
    .catch(err => err))
    this.appointments = await (data).map(el => {
        el.aptId = this.aptIndex
        this.aptIndex++
        return el
      }
      )
      console.log(this.appointments)
  },
  components: {
    AppointmentsList
  },
  methods: {
    removeItem: function(apt){
      
      this.appointments = _.without(this.appointments, apt)

    },
    editItem: function(id, fild, text){
      const aptIndex = _.findIndex(this.appointments, {
        aptId: id
      })

      this.appointments[aptIndex][fild] = text
    }
  },
};
</script>


<style>
@import "https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.1.1/css/all.min.css";
</style>
