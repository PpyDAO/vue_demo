<template>
  <div style="margin-left: 120px">
    <!-- <vueSlider ref="slider3" v-bind="demo3" v-model="demo3.value"></vueSlider>
    <div>{{sonmsg}}</div>
    <table-ext :parentmsg="msg" @func="fatherClick"></table-ext> -->

    <!-- <my-menu :items="items"></my-menu> -->
    <div id="myChart" :style="{width: '400px', height: '300px'}"></div>
  </div>
</template>

<script>
import vueSlider from "./vueSlider.vue";
import tableExt from "./TableExt.vue";
import MyMenu from "./MyMenu.vue";
export default {
  name: "HelloWorld",
  components: {
    vueSlider,
    tableExt,
    MyMenu
  },
  data() {
    return {
      items: [
        {
          lable: "小学",
          grade: [
            {
              lable: "一年级",
              class: [
                {
                  lable: "一年级一班",
                  active: true
                },
                {
                  lable: "一年级二班",
                  active: true
                },
                {
                  lable: "一年级三班",
                  active: false
                }
              ]
            },
            {
              lable: "二年级",
              class: [
                {
                  lable: "二年级一班",
                  active: false
                },
                {
                  lable: "二年级二班",
                  active: false
                },
                {
                  lable: "二年级三班",
                  active: false
                }
              ]
            }
          ]
        },
        {
          lable: "初中",
          grade: [
            {
              lable: "初一",
              class: [
                {
                  lable: "初一一班",
                  active: false
                },
                {
                  lable: "初一二班",
                  active: false
                },
                {
                  lable: "初一三班",
                  active: false
                }
              ]
            },
            {
              lable: "初二",
              class: [
                {
                  lable: "初二一班",
                  active: false
                },
                {
                  lable: "初二二班",
                  active: false
                },
                {
                  lable: "初二三班",
                  active: false
                }
              ]
            }
          ]
        }
      ],

      demo3: {
        value: [0, 100],
        width: 16,
        height: 500,
        dotSize: 25,
        min: 0,
        max: 500,
        disabled: false,
        show: true,
        useKeyboard: true,
        tooltip: "always",
        formatter: "{value}",
        enableCross: false,
        mergeFormatter: "{value1} ~ {value2}",
        direction: "vertical",
        clickable: false,
        bgStyle: {
          backgroundColor: "#35495e",
          boxShadow: "inset 0.5px 0.5px 3px 1px rgba(0,0,0,.36)"
        },
        tooltipStyle: [
          {
            backgroundColor: "#35495e",
            borderColor: "#35495e"
          },
          {
            backgroundColor: "#41b883",
            borderColor: "#41b883"
          }
        ],
        processEndStyle: {
          backgroundColor: "#DC143C"
        },
        processStyle: {
          backgroundColor: "#41b883"
        }
      },
      msg: "父组件的数据",
      sonmsg: "old msg",
      flag: true
    };
  },
  created() {},
  mounted() {
    this.drawLine();
  },
  methods: {
    fatherClick: function(params) {
      if (this.flag) {
        this.sonmsg = params;
        this.flag = false;
      } else {
        this.sonmsg = "old msg";
        this.flag = true;
      }
    },
    drawLine: function() {
      // 基于准备好的dom，初始化echarts实例
      let myChart = this.$echarts.init(document.getElementById("myChart"));
      // 绘制图表
      var echartData = [
        {
          value: 11,
          name: "高"
        },
        {
          value: 10,
          name: "中"
        },
        {
          value: 20,
          name: "低"
        }
      ];
      myChart.setOption({
        tooltip: {
          trigger: "item",
          formatter: " {b}: {c} ({d}%)"
        },
        color: ["#c00000", "#d78b3d", "#00b050"],
        legend: {
          selectedMode: false,
          formatter: function(name) {
            var tip = "总数：";
            var total = 0;
            echartData.forEach(function(value, index, array) {
              total += value.value;
            });
            return "{tip|" + tip + "} {total|" + total + "}";
          },
          data: [echartData[0]],
          top: "center",
          left: "center",
          icon: "none",
          align: "center",
          textStyle: {
            rich: {
              tip: {
                color: "#293c55",
                fontSize: 18,
                align: "center"
              },
              total: {
                color: "#ffc72b",
                fontSize: 18,
                align: "center",
                padding: [0, 0, 6, 0]
              }
            }
          }
        },
        series: [
          {
            name: "访问来源",
            type: "pie",
            radius: ["35%", "45%"],
            label: {
              normal: {
                formatter: " {b|{b}：}{c} {per|{d}%} ",
                backgroundColor: "#eee",
                borderColor: "#aaa",
                borderWidth: 1,
                borderRadius: 4,
                rich: {
                  b: {
                    fontSize: 14,
                    lineHeight: 30
                  },
                  per: {
                    color: "#eee",
                    backgroundColor: "#334455",
                    padding: [2, 4],
                    borderRadius: 2
                  }
                }
              }
            },
            data: echartData
          }
        ]
      });
    }

    // drawLine: function() {
    //   // 基于准备好的dom，初始化echarts实例
    //   let myChart = this.$echarts.init(document.getElementById("myChart"));
    //   // 绘制图表
    //   myChart.setOption({
    //     title: {
    //       text: "在Vue中使用echarts"
    //     },
    //     tooltip: {},
    //     xAxis: {
    //       data: ["衬衫", "羊毛衫", "雪纺衫", "裤子", "高跟鞋", "袜子"]
    //     },

    //     yAxis: {},
    //     series: [
    //       {
    //         name: "销量",
    //         type: "bar",
    //         data: [5, 20, 36, 10, 10, 20]
    //       }
    //     ]
    //   });
    // }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
