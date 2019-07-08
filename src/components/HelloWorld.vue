<template>
  <div>
    <h1> {{ loadingComplete() }}</h1>
    <h1>{{ title }}</h1>
      <Calendar v-bind:calendarParts="calendarParts"/>
      <Time nickname="SaintMiner"/>
  </div>
</template>

<script>
import Calendar from './Calendar.vue';
import Time from './Time.vue';

export default {
  name: 'HelloWorld',
  props: {
    title: String,
  },

  components: {
    Calendar,
    Time
  },

  data() {
        return {
            calendarParts: [
                {partName: "Day", partValue: 1, partDescription: "This is a common day ^.^! My diapazone: [1-31(max)]", showDescr: false},
                {partName: "Week", partValue: 4, partDescription: "I am week like a normal week", showDescr: false},
                {partName: "Month", partValue: 6, partDescription: "Month - Yes (-_-)/", showDescr: false}
            ]
            
        }
  },

  methods: {
    loadingComplete: function() {
      return "AAAAAAAAAAAAAAAAAAA... Loading complete!!!"
    },

    todayDate: function() {
      return new Date(Date.now()).getFullYear();
      
      
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  
</style>
