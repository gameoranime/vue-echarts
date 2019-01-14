<template>
  <div id="app">
    <h1>echarts练习</h1>
    <div id="main" style="width:1200px;height:800px;"></div>
    <div class="container"></div>
  </div>
</template>

<script>
import echarts from "./lib/echarts.js";
import FirstChart from "./components/FirstChart.js";
export default {
  name: "app",
  data() {
    return {
      echartsObj: undefined,
      option: undefined
    };
  },
  created() {
    console.log(echarts);
  },
  mounted() {
    this.initChart();
    this.bindEvent()
    // this.mount1()
  },
  methods: {
    initChart() {
      this.echartsObj = echarts.init(document.getElementById("main"));
      console.log(this.echartsObj);
      this.initData()
      this.echartsObj.setOption(this.option);
    },
    initData() {
      this.option = {
        // 取消动画
        animation: false,
        tooltip: {
          show: true
        },
        legend: {
          data: ["蒸发量", "降水量", "平均温度"]
        },
        xAxis: [
          {
            type: "category",
            data: [
              "1月",
              "2月",
              "3月",
              "4月",
              "5月",
              "6月",
              "7月",
              "8月",
              "9月",
              "10月",
              "11月",
              "12月"
            ],
            axisPointer: {
              type: "shadow"
            }
          }
        ],
        yAxis: [
          {
            type: "value",
            name: "水量",
            min: 0,
            max: 250,
            interval: 50,
            axisLabel: {
              formatter: "{value} ml"
            }
          }
        ],
        series: [
          {
            name: "蒸发量",
            type: "bar",
            data: [
              2.0,
              4.9,
              7.0,
              23.2,
              25.6,
              76.7,
              135.6,
              162.2,
              32.6,
              20.0,
              6.4,
              3.3
            ]
          },
          {
            name: "降水量",
            type: "bar",
            data: [
              2.6,
              5.9,
              9.0,
              26.4,
              28.7,
              70.7,
              175.6,
              182.2,
              48.7,
              18.8,
              6.0,
              2.3
            ]
          }
        ]
      };
    },
    mount1() {
      var fc = new FirstChart();
      fc._view.$mount(".container");
      console.log(this);
      console.log(fc._view);
    },
    bindEvent(){
      // 绑定事件,点击柱状图
      this.echartsObj.on('click',opt =>{
        console.log(opt);
        
      })

      // 点击legend,不隐藏,修改柱状图颜色,表示高亮与不高亮
      this.echartsObj.on('legendselectchanged',opt => {
        console.log(opt);
        this.echartsObj.dispatchAction({
          type: 'legendSelect',
          name: opt.name
        })
        
        
      })
    }
  }
};
</script>

<style>
</style>
