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
      speed: 5,
      loop: true,
      channels: 4,
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
    }, 0);

    this.addItem();
  },
  methods: {
    getRandomNumberByRange(start, end) {
      return Math.floor(Math.random() * (end - start) + start);
    },

    addItem() {
      setInterval(() => {
        this.$refs.barrage.add({
          icon: `https://backet-flb-face-search.oss-cn-hongkong.aliyuncs.com/da605649c4f44eb9a141cc549d3a322d_face_1.jpg`,
          content: "王朋，祝你新年快乐呀:君不见，黄河之水天上来，奔流到海不复回 ." + this.currentId++,
          color: "green"
        });
        
      },0);
    }
  }
};
</script>
<style lang="less">
.barrage {
  position: fixed;
  top: 50px;
  width: 100%;
  height: 100%;
  z-index: 1;
  background: #fff;
}

body {
  margin: 0;
  padding: 0;
  font-size: 14px;
}

.add {
  cursor: pointer;
  position: absolute;
  z-index: 333;
  color: red;
}
</style>
