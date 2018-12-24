<template>
  <div id="app">
    <h1>echarts练习</h1>
    <div id="main" style="width:600px;height:400px;"></div>
    <div class="container"></div>
  </div>
</template>

<script>
import echarts from "./lib/echarts.js";
import FirstChart from "./components/FirstChart.js"
export default {
  name: "app",
  data() {
    return {
      echartsObj: undefined
    };
  },
  created() {
    console.log(echarts);
    
  },
  mounted() {
    this.initChart()
    this.mount1()
  },
  methods:{
    initChart(){
      this.echartsObj = echarts.init(document.getElementById("main"));
      console.log(this.echartsObj);
      
      this.echartsObj.setOption({
        title: {
          text: "ECharts 入门示例"
        },
        tooltip: {},
        xAxis: {
          data: ["衬衫", "羊毛衫", "雪纺衫", "裤子", "高跟鞋", "袜子"]
        },
        yAxis: {},
        series: [
          {
            name: "销量",
            type: "bar",
            data: [5, 20, 36, 10, 10, 20]
          }
        ]
      });
    },
    mount1(){
      var fc = new FirstChart()
      fc._view.$mount('.container')
      console.log(this);
      console.log(fc._view);
      
      
      
    }
  }
};
</script>

<style>
</style>
