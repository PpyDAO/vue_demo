<template>
    <div class="wrapper">
        <div sytle="float: left">
            <div v-for="item in items">
                <span @click="clickItem(item,$event)">{{item.lable}}</span>
            </div>
        </div>
        <div :style="{'padding-left': aaa}">
            <div v-for="grade in grades.grade">
                <span>{{grade.lable}}</span>
            </div>
        </div>
    </div>
</template>

<script>
export default {
  components: {},
  props: ["items"],
  data() {
    return {
      grades: [],
      aaa: 0
    };
  },
  watch: {},
  computed: {},
  methods: {
    clickItem(oItem, oEvent) {
      this.aaa = oEvent.target.offsetWidth + 5
      console.log(this.aaa);
      this.grades = oItem;
    }
  },
  created() {},
  mounted() {}
};
</script>
<style scoped>
</style>