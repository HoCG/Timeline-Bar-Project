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
      timelineData: [  
        [
          { type: 'string', id: 'Term' },
          { type: 'string', id: 'Name' },
          { type: 'string', role: 'style' },
          { type: 'date', id: 'Start' },
          { type: 'date', id: 'End' },
        ]
      ]
      ,
      timelineOptions: {
        timeline: {
          rowLabelStyle: { fontName: "Ariel"},
          colorByRowLabel: true
        },
        tooltip: { textStyle: { fontName: "Ariel", fontSize: 14} },
      },
    };
  },
  
  mounted: function () {
    //변수 선언부
    let titleArray = []; //몇번째 줄에 타이틀이 무엇인지를 정의(커리어 종류)
    let title_of_Color = [[255, 0, 0], [51, 102, 255], [253, 220, 0]];
    let title_Number_In_One_Line = []; //하나의 라인에 몇개의 라벨이 들어있는지를 판별.
    let title_Number_In_One_Line_Current = []; //현재 이라인에 라벨의 위치

    this.Initialization_Of_title_Number_In_One_Line(title_Number_In_One_Line, title_Number_In_One_Line_Current);
    this.titleArray_Pusher(titleArray, title_Number_In_One_Line);
    this.Input_Into_timelineData(titleArray, title_of_Color, title_Number_In_One_Line, title_Number_In_One_Line_Current);
  },

  methods: {
    Initialization_Of_title_Number_In_One_Line(titleNumberInOneLine, title_Number_In_One_Line_Current){
      for(let i = 0; i < timelineJson.items.length; ++i){
        titleNumberInOneLine[i] = 0;
        title_Number_In_One_Line_Current[i] = 0;
      }
    },

    titleArray_Pusher(titleArray, title_Number_In_One_Line){
      for(let i = 0; i < timelineJson.items.length; ++i){
        let title = String(timelineJson.items[i].title);
        if(!titleArray.includes(title)){
          titleArray.push(title);
        }
        ++title_Number_In_One_Line[titleArray.indexOf(title)];
      }
    },

    Input_Into_timelineData(titleArray, title_of_Color, title_Number_In_One_Line, title_Number_In_One_Line_Current){
      let startYear;
      let startMonth;
      let startDate;
      let endYear;
      let endMonth;
      let endDate;
      for(let i = 0; i < timelineJson.items.length; ++i){
      //start
        let timelineStart = parseInt(timelineJson.items[i].start);
        [startYear, startMonth, startDate] = this.Make_YearMonthDate(timelineStart);
        //console.log(startDate);
        timelineJson.items[i].start = new Date(startYear, startMonth, startDate);

        //end
        let timelineEnd = parseInt(timelineJson.items[i].end);
        [endYear, endMonth, endDate] = this.Make_YearMonthDate(timelineEnd);
        timelineJson.items[i].end = new Date(endYear, endMonth, endDate);

        //console.log(endDate);
        let title = String(timelineJson.items[i].title);
        ++title_Number_In_One_Line_Current[titleArray.indexOf(title)];
        this.timelineData.push(
          [ timelineJson.items[i].title
          , timelineJson.items[i].labelname
          , this.RGB_Calculater(title_of_Color[titleArray.indexOf(title)], title_Number_In_One_Line[titleArray.indexOf(title)], title_Number_In_One_Line_Current[titleArray.indexOf(title)])
          , timelineJson.items[i].start
          , timelineJson.items[i].end ]
        );
      }
    },

    RGB_Calculater([Red, Green, Blue], title_Number_In_One_Line, title_Number_In_One_Line_Current){
      if(Red === 255){
        Red = parseInt((2 * Red / 5) + ((3 * Red / 5) / title_Number_In_One_Line) * title_Number_In_One_Line_Current)
      }
      else if(Green >= 220){
        Green = parseInt((2 * Green / 3) + ((Green / 3) / title_Number_In_One_Line) * title_Number_In_One_Line_Current)
      }
      else if(Blue === 255){
        Blue = parseInt((2 * Blue / 5) + ((3 * Blue / 5) / title_Number_In_One_Line) * title_Number_In_One_Line_Current)
      }
      return "rgb("+ Red +","+ Green +","+ Blue +")";
    },

    Make_YearMonthDate(timelineNumber){
      let Year = parseInt(timelineNumber / 10000);
      let Month = parseInt((timelineNumber % 10000) / 100);
      let Date = parseInt((timelineNumber % 100));
      return [Year, Month, Date]
    }
  }
};
</script>
<style>
text{
  font-weight: bold !important;
  font-style: inherit !important;
}
rect{
  stroke-width: 1; /*!important;*/
  stroke: black; /*!important;*/
}
</style>

