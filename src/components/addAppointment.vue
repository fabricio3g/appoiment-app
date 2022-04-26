<template>
  <div class="container">
    <button @click="hiddenpanel = !hiddenpanel" class="btn btn-primary w-100 text-start rounded mb-5"><i class="fa fa-add"></i> Add appointment</button>
    <form @submit.prevent="requestAdd" class="mb-5" :class="{ 'd-none': hiddenpanel }">
  <div class="mb-3">
    <label for="exampleInputEmail1" class="form-label">Pet's Name</label>
    <input name="petName" v-model="formData.petName" type="text" class="form-control" />
  </div>
  <div class="mb-3">
    <label for="exampleInputPassword1" class="form-label">Pet Owner</label>
    <input name="petOwner" v-model="formData.petOwner" type="text" class="form-control" >
  </div>
  <div class="mb-3">
    <label for="exampleInputPassword1" class="form-label">Date</label>
    <input  name="date" v-model="formData.date" type="date" class="form-control" >
  </div>
   <div class="mb-3">
    <label for="exampleInputPassword1" class="form-label">Date</label>
    <input name="time" v-model="formData.time"  type="time" class="form-control" >
  </div>
    <div class="mb-3">
    <label for="exampleInputPassword1" class="form-label">Notes</label>
    <input name="time" v-model="formData.aptNotes"  type="text" class="form-control" >
  </div>

  <button type="submit" class="btn btn-primary">Submit</button>
</form>
  </div>
</template>
<script>

export default{
    name: "addAppointment",
    data: ()=> {
        return {
            formData: [],
            hiddenpanel: true
        }
    }
    ,
        methods: {
            requestAdd: ()=>{
                this.formData = {
                    petName: this.formData.petName,
                    petOwner: this.formData.petOwner,
                    aptDate: this.formDate.date + " " + this.formData.time,
                    aptNotes: this.formDate.aptNotes
                }
            }
        }
}

</script>