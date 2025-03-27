<template>
<div>
    <label for="start-date">Start Date:</label>
    <input type="date" id="start-date" v-model="startDate">
    <label for="end-date">End Date:</label>
    <input type="date" id="end-date" v-model="endDate">
    <p>Selected Range: {{ startDate }} - {{ endDate }}</p>
    <button @click="listNeos">List NEOs</button>
    <NeoComponent :startDate="startDate" :endDate="endDate" v-if="datesEntered"/>
</div>


</template>

<script>
import NeoComponent from '../components/NeoComponent.vue'


export default {
    components: { NeoComponent },

    data() {
        return {
           startDate: '',
           endDate: '',
           datesEntered: false
        }
    }, 
    methods: {
        listNeos() {
            this.datesEntered = true
        }
    }
    
}



</script>

<style>



</style>