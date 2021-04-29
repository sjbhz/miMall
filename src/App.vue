<template>
  <div id="app">
    <router-view></router-view>
  </div>
</template>

<script>
// import storage from "./storage/index";
export default {
  name: "App",
  components: {},
  data() {
    return {
      res: {}
    };
  },
  mounted() {
    this.getUser();
    this.getCartCount();
    // storage.setItem("a", 1);
    // storage.setItem("abc", { a: 1 }, "user");
    // storage.clear("a");
    // storage.clear("a", "user");
    //本地加载请求静态json文件
    // this.axios.get("/mock/user/login.json").then(res => {
    //   this.res = res.data;
    // });
    //easy-mock平台实现数据mock
    // this.axios.get("/user/login").then(res => {
    //   this.res = res.data;
    // });
    //本地集成mockjs
    // this.axios.get("/user/login").then(res => {
    //   this.res = res.data;
    // });
  },
  methods: {
    getUser() {
      this.axios.get("/user").then(res => {
        //to-do 保存到vuex
        this.$store.dispatch("saveUserName", res.username);
      });
    },
    getCartCount() {
      this.axios.get("/carts/products/sum").then(res => {
        this.$store.dispatch("saveCartCount", res);
      });
    }
  }
};
</script>

<style lang="scss">
@import "./assets/scss/reset.scss";
@import "./assets/scss/config.scss";
@import "./assets/scss/button.scss";
</style>
