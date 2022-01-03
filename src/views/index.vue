<template>
  <div class="app">
    <div :style="indexStyle" ref="index">
      <mi-load :load="load"></mi-load>
      <mi-header @searchEvent="searchHandle" :opac="headerOpacity"></mi-header>
      <div v-show="a">
        <mi-menu :menu="menu"></mi-menu>
        <div style="width: 100%; height: 60px; background: #eee"></div>
        <mi-footer></mi-footer>
      </div>
    </div>
  </div>
</template>

<script>
import load from "../components/loading";
import header from "../components/index/header";
import menu from "../components/index/menu";
import footer from "../components/index/footer";
import data from "../../data";

export default {
  name: "index",
  components: {
    "mi-load": load,
    "mi-header": header,
    "mi-menu": menu,
    "mi-footer": footer,
  },
  created() {
    const me = this;
    setTimeout(function () {
      me.a = true;
    }, 2000);
    me.banner = data.banner;
    me.menu = data.menu;
    me.body = data;
    me.bannerList = data.banner.bannerTop;
  },
  mounted() {
    const me = this;
    let screenSize = {
      screenSize() {
        let width = window.screen.width;
        let height = window.screen.height;
        return { width: width, height: height };
      },
    };
    console.log(screenSize);
    this.c_height = 0.711 * screenSize.width;
    const height = (screenSize.width * 256) / 360;
    this.$refs.index.onscroll = function () {
      me.headerOpacity = this.scrollTop / height;
    };
  },
  data() {
    let screenSize = {
      screenSize() {
        let width = window.screen.width;
        let height = window.screen.height;
        return { width: width, height: height };
      },
    };
    return {
      banner: {},
      menu: {},
      body: {},
      bannerList: [],
      scrollX: 0,
      scrollY: 0,
      searchState: false,
      headOpac: "",
      load: false,
      a: false,
      c_height: 0,
      indexStyle: {
        height: screenSize.height + "px",
        "overflow-y": "scroll",
        width: "100%",
      },
      headerOpacity: 0,
    };
  },
  methods: {
    searchHandle(Boolean) {
      if (Boolean) {
        this.searchState = true;
      } else {
        this.searchState = false;
      }
    },
  },
};
</script>

<style scoped>
.app {
  background: #fff;
  overflow-y: scroll;
  width: 100%;
  height: 100%;
}
</style>
