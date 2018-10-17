<template>
    <div class="wrapper">
        <h1 href="" @click="click">这是子组件 --- {{parentmsg}} {{content}}</h1>
    </div>
</template>

<script>
export default {
  components: {},
  props: ["parentmsg"],
  data() {
    return {
      sonmsg: "hello world",
      content: "qqq",
      flag: true
    };
  },
  watch: {},
  computed: {},
  methods: {
    click: function() {
      this.$emit("func", this.sonmsg);
      if (this.flag) {
        this.content = "www";
        this.flag = false;
      } else {
        this.content = "qqq";
        this.flag = true;
      }
    }
  },
  created() {},
  mounted() {}
};
</script>
<style scoped>
</style>