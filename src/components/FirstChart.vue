<template>
    <div>
        <h1>text</h1>
        <div id="main1" style="width:600px;height:400px;"></div>
    </div>
</template>

<script>
import vue from "vue";
import echarts from "../lib/echarts.js";
export default vue.extend({
  data() {
    return {
      echartsObj: undefined
    };
  },
  mounted(){
      this.initChart()
  },
  methods: {
    initChart() {
      this.echartsObj = echarts.init(document.getElementById("main1"));
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
    }
  }
});
</script>