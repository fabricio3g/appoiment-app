<template>
  <div class="container">
    <button @click="hiddenpanel = !hiddenpanel" class="btn bg-black text-white w-100 text-start rounded-top mb-5"><i class="fa fa-add"></i> Add appointment</button>
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
    <input  name="aptDate" v-model="formData.aptDate" type="date" class="form-control" >
  </div>
   <div class="mb-3">
    <label for="exampleInputPassword1" class="form-label">Date</label>
    <input name="aptTime" v-model="formData.aptTime"  type="time" class="form-control" >
  </div>
    <div class="mb-3">
    <label for="exampleInputPassword1" class="form-label">Notes</label>
    <input name="aptNotes" v-model="formData.aptNotes"  type="text" class="form-control" >
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
            requestAdd: function()    {
                this.formData = {
                    petName: this.formData.petName,
                    petOwner: this.formData.petOwner,
                    aptDate: new String(this.formData.aptDate) + " " + this.formData.aptTime,
                    aptNotes: this.formData.aptNotes
                }
                this.$emit('add', this.formData)
                this.formData = []
                this.hiddenpanel = true 
            }
        }
}

</script>