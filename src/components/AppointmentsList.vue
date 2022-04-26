<template>
    
    <div class='card pt-3 px-3 my-2'  v-for="item in appointments" :key="item.aptId" >
    <div class='d-flex flex-row text-muted'>
      <small>{{formatedDate(item.aptDate)}}</small>
    </div>
    <h4 contenteditable @blur="$emit('edit', item.aptId, 'petName', $event.target.innerText)" >{{item.petName}}</h4>
    <p>{{item.aptNotes}}</p>
    <div><small class='text-muted'>Pet Owner: </small> <b class=''>{{item.petOwner}}</b>
    </div>
    <div class='d-flex align-self-end'>
      <button @click="$emit('remove',item)" class='btn btn-danger mb-3'>
      <i class='fa fa-trash '></i>
      </button>
    </div>
  </div>
</template>
<script>
import moment from 'moment'
export default{
    name: "AppointmentsList",
    props: ["appointments"],
    methods: {
      formatedDate: (date)=>{
        return moment(new Date(date)).format("MM-DD-YY, h:mm a")
      }
    },
   
}
</script>