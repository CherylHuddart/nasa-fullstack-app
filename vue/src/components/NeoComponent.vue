<template>


</template>

<script>
import service from '../services/AuthService'

export default {
    props: {
        startDate: '',
        endDate: ''
    },
    data(){
        return {
            neoList: []
        }
    },
    created(){
        service.getNeos(this.startDate, this.endDate)
        .then((response) => {
            // console.log(response);
            this.neoList = response.data;
        })
    }
}
</script>

<style>
</style>