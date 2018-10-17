<template>
    <div class="wrapper">
        <vueSlider ref="slider3" v-bind="sliderData" v-model="sliderData.value"></vueSlider>
    </div>
</template>

<script>
export default {
  components: {},
  props: [],
  data() {
    return {
        sliderData: {
        value: [0, 100],
        width: 16,
        height: 200,
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
      annotation: {
          width: '组件宽度',
          height: '组件高度',
          dotWidth: '滑块宽度',
          dotHeight: '滑块高度',
          direction: '组件方向',
          eventType: '事件类型',
          dotSize: '滑块大小',
          min: '最小值',
          max: '最大值',
          interval: '分段间隔',
          debug: '是否为开发环境（打印错误）',
          fixed: '是否固定距离',
          processDragable: '进度条是否可拖拽（只限范围模式）',
          disabled: '是否不可用',
          clickable: '是否可点击的',
          show: '是否显示组件',
          realTime: '是否实时计算组件布局',
          speed: '动画速度',
          tooltip: '是否显示工具提示',
          lazy: '是否在拖拽结束后同步值',
          useKeyboard: '是否使用键盘控制',
          tooltipDir: '工具提示方向',
          tooltipStyle: '工具提示样式',
          piecewise: '是否显示分段样式',
          reverse: '是否反向组件',
          formatter: '格式化tooltip的值',
          processStyle: '进度条样式',
          sliderStyle: '滑块样式',
          bgStyle: '组件背景样式',
          piecewiseStyle: '分割点的样式',
          disabledStyle: '组件禁用状态下样式',
          focusStyle: '键盘控制时，算滑块获得焦点时样式',
          startAnimation: '是否开启初始动画',
          value: '值',
          enableCross: '在范围模式中，是否允许交叉'
        }
    };
  },
  watch: {},
  computed: {},
  methods: {},
  created() {},
  mounted() {}
};
</script>
<style scoped>
</style>