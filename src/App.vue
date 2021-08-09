<template>
  <div id="app">
    <GChart
      type="Timeline"
      :settings="{ packages: ['timeline'],
      language: 'ko' }"
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
   for(let i = 0; i < timelineJson.items.length; ++i){
     //start
     let timelineStart = parseInt(timelineJson.items[i].start);
     let startYear = parseInt(timelineStart / 10000);
     //console.log(startYear);
     let startMonth = parseInt((timelineStart % 10000) / 100);
     //console.log(startMonth);
     let startDate = parseInt((timelineStart % 100));
     //console.log(startDate);
     timelineJson.items[i].start = new Date(startYear, startMonth, startDate);
     //end
     let timelineEnd = parseInt(timelineJson.items[i].end);
     let endYear = parseInt(timelineEnd / 10000);
     //console.log(endYear);
     let endMonth = parseInt((timelineEnd % 10000) / 100);
     //console.log(endMonth);
     let endDate = parseInt(timelineEnd % 100);
     //console.log(endDate);
     timelineJson.items[i].end = new Date(endYear, endMonth, endDate);

     this.timelineData.push([timelineJson.items[i].title, timelineJson.items[i].labelname, 
     timelineJson.items[i].start, timelineJson.items[i].end])
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

