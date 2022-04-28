<template>

<div class="container my-5">
<input v-model="searchTerm" type="text" id="inputPassword5" class="form-control" aria-describedby="passwordHelpBlock" placeholder="Search something...">

</div>

</template>

<script>

export default{
    name: "searchAppointment",
    data(){
        return {
            searchTerm: ""
        }
    },
    watch: {
        searchTerm: function(){
            this.$emit('searchRecords', this.searchTerm)
        }
    }
}

</script>