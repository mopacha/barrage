<template>
  <div id="app">
    <barrage
      ref="barrage"
      class="barrage"
      :barrage-list="barrageList"
      :speed="speed"
      :loop="loop"
      :channels="channels"
      :background="background"
      :border-color="borderColor"
    />
    <canvas ref="canvas"></canvas>
  </div>
</template>

<script>
import Barrage from "./views/src/index";
//    import Barrage from 'vue-barrage'
export default {
  name: "app",
  components: {
    Barrage
  },
  data() {
    return {
      userImg: require("./imgs/1.jpg"),
      msg: "评论信息评论信息",
      barrageIsShow: true,
      currentId: 0,
      barrageList: [],
      speed: 4,
      loop: true,
      channels: 5,
      background: "#FFFFFF",
      borderColor: "rgb(233,195,237)"
    };
  },
  mounted() {
    setTimeout(() => {
      this.barrageList = [
        {
          icon: this.userImg,
          content: "1试数据测试数测试数据数测试数据",
          color: "orange"
        },
        {
          icon: this.userImg,
          content: "2数据测试数据测试数据测试数据测试数据测试数据",
          color: "orange"
        },
        {
          icon: this.userImg,
          content: "3测试数据测试数据测试数据测试数据测试数据数据测试数据",
          color: "red"
        },
        {
          icon: this.userImg,
          content: "4试数据测测试数据测试数据测试数据测试数据测试数据试据",
          color: "blue"
        },
        {
          content: "5测试数据测试数据测试数据测试数据测试数据",
          color: "green"
        },
        {
          content: "6测试数据测试数据数据测试数据",
          color: "orange"
        }
      ];
    }, 500);
  },
  methods: {
    add() {
      this.$refs.barrage.add({
        content: "增加一条新的弹幕增加一条新的弹幕",
        color: "white"
      });
    }
  }
};
</script>
<style lang="less">
.barrage {
  position: fixed;
  top: 0;
  width: 100%;
  height:100%;
  z-index: 1;
  background: rgba(70, 126, 120);
}

body {
  margin: 0;
  padding: 0;
  font-size: 20px;
}
</style>
