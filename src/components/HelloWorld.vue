<template>
  <div style="margin-left: 500px">
    <vueSlider ref="slider3" v-bind="demo3" v-model="demo3.value"></vueSlider>
    <div>{{sonmsg}}</div>
    <table-ext :parentmsg="msg" @func="fatherClick"></table-ext>
  </div>
</template>

<script>
import vueSlider from "./vueSlider.vue";
import tableExt from "./TableExt.vue";
export default {
  name: "HelloWorld",
  components: {
    vueSlider,
    tableExt
  },
  data() {
    return {
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
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
