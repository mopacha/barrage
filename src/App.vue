<template>
  <div id="app">
    <div class="wall">
      <div class="qin">
        <img :src="qinImg" alt="" />
      </div>
      <div class="happy">
        <img :src="happyImg" alt="" />
      </div>

      <div class="duilian">
        <img :src="duilianImg" alt="" />
      </div>

      <div class="canvasWrap">
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
    </div>
  </div>
</template>

<script>
import Barrage from "./views/index";
//    import Barrage from 'vue-barrage'
export default {
  name: "app",
  components: {
    Barrage
  },
  data() {
    return {
      happyImg: require("./imgs/happy.png"),
      duilianImg: require("./imgs/duilian.png"),
      qinImg: require("./imgs/qin.png"),
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
          color: "#fff",
          hat: "left"
        },
        {
          icon: this.userImg,
          content: "2数据测试数据测试数据测试数据测试数据测试数据",
          color: "#fff",
          hat: "left"
        },
        {
          icon: this.userImg,
          content: "3测试数据测试数据测试数据测试数据测试数据数据测试数据",
          color: "blue",
          hat: "right"
        },
        {
          icon: this.userImg,
          content: "4试数据测测试数据测试数据测试数据测试数据测试数据试据",
          color: "blue",
          hat: "right"
        },
        {
          content: "5测试数据测试数据测试数据测试数据测试数据",
          color: "green",
          hat: "right"
        },
        {
          content: "6测试数据测试数据数据测试数据",
          color: "orange",
          hat: "right"
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
          content: "王朋，祝你新年快乐呀" + this.currentId++,
          color: "#fff",
          hat: this.getRandomNumberByRange(1, 10) > 5 ? "left" : "right"
        });
      }, 0);
    }
  }
};
</script>
<style lang="less">
.wall {
  padding-top: 80px;
  height: 100%;
  .qin {
    text-align: center;
    img {
      width: 137px;
    }
  }
  .happy {
    text-align: center;
    margin-top: 15px;
    img {
      width: 363px;
    }
  }
  .duilian {
    position: absolute;
    z-index: 0;
    top: 100px;
    right: 30px;
    img {
      width: 100px;
    }
  }
}

.canvasWrap{
  position: relative;
  z-index: 100;
}

.barrage2 {
  position: fixed;
  top: 0px;
  width: 100%;
  height: 100%;
  z-index: 1;
}
</style>
