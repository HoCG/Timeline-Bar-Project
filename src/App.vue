<template>
  <div id="app">
    <GChart
      type="Timeline"
      :settings="{ packages: ['timeline'] }"
      :data="timelineData"
      :options="timelineOptions"
    />
  </div>
</template>

<script>
import { GChart } from "vue-google-charts";
import timelineJson from './assets/timelineTest.json'
export default {
  name: "App",
  components: {
    GChart,
  },

  data() {
    return {
      timelineData: []
      ,
      timelineOptions: {
        timeline: {
          rowLabelStyle: { fontName: "Ariel"},
        },
        colors: ["#E74C3C", "#2C3E50", "#2980B9"],
        tooltip: { textStyle: { fontName: "Ariel", fontSize: 14} },
      },
    };
  },
  
  mounted: function () {
   for(let i = 0; i < timelineJson.timelineData.length; ++i){
     //start
     let startYear = parseInt(timelineJson.timelineData[i].start / 10000);
     //console.log(startYear);
     let startMonth = parseInt((timelineJson.timelineData[i].start % 10000) / 100);
     //console.log(startMonth);
     let startDate = parseInt((timelineJson.timelineData[i].start % 100));
     //console.log(startDate);
     timelineJson.timelineData[i].start = new Date(startYear, startMonth, startDate);
     //end
     let endYear = parseInt(timelineJson.timelineData[i].end / 10000);
     //console.log(endYear);
     let endMonth = parseInt((timelineJson.timelineData[i].end % 10000) / 100);
     //console.log(endMonth);
     let endDate = parseInt(timelineJson.timelineData[i].end % 100);
     //console.log(endDate);
     timelineJson.timelineData[i].end = new Date(endYear, endMonth, endDate);

     this.timelineData.push([timelineJson.timelineData[i].name, timelineJson.timelineData[i].labelname, 
     timelineJson.timelineData[i].start, timelineJson.timelineData[i].end])
   }
  }
};
</script>
<style>
text{
  font-weight: bold !important;
  font-style: inherit !important;
}
</style>

