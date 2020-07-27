<template>
  <div>
    <el-page-header @back="goBack" content="母婴安康"></el-page-header>
    <!-- <el-divider></el-divider> -->
    <el-tabs v-model="activeName">
      <el-tab-pane label="产品特色" name="first">
        <el-image :src="urlPro" style="width:300%"></el-image>
      </el-tab-pane>
      <el-tab-pane label="快速理赔" name="second">
        <el-image :src="urlQuick" style="width:300%"></el-image>
      </el-tab-pane>
      <el-tab-pane label="常见问题" name="third">
        <el-image :src="urlQues" style="width:300%"></el-image>
      </el-tab-pane>
    </el-tabs>
  </div>
</template>

<script>
export default {
  data() {
    return {
      activeName: "first",
      urlPro: require("../assets/product.png"),
      urlQuick: require("../assets/quick.png"),
      urlQues: require("../assets/question.png")
    };
  },
  methods: {
    goBack() {
      console.log("go back");
    }
  }
};
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.el-page-header {
  padding-left: 5%;
}
.el-page-header__content {
  font-size: 22px;
}
.el-divider--horizontal {
  margin: 5px 0;
}
.el-tabs__header {
  margin: 0;
}
.el-tabs,
.el-tabs--top  {
  width: 100vw;
  color: #f96f89;
  margin: 6px 0;
}
.el-tab-pane,
.el-tabs__item {
  width: 33.33333vw;
  color: black;
  font-size: 18px;
  padding: 0 0;
}
.el-tabs__active-bar {
  background-color: #f96f89;
}
.el-tabs__item:hover {
  color: #f96f89;
}
.el-tabs__item.is-active {
  color: #f96f89;
}
</style>