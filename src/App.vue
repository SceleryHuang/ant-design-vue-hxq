<template>
  <div id="app">
    <a-locale-provider :locale="locale">
      <router-view></router-view>
    </a-locale-provider>
  </div>
</template>
<script>
import zhCN from "ant-design-vue/lib/locale-provider/zh_CN";
import enUs from "ant-design-vue/lib/locale-provider/en_US";
import moment from "moment";
import "moment/locale/zh-cn";

export default {
  data() {
    return {
      locale: zhCN
    };
  },
  watch: {
    "$route.query.locale": function(val) {
      this.locale = val === "enUS" ? enUs : zhCN;
      moment.locale(val === "enUS" ? "en" : "zh-cn");
    }
  }
};
</script>
<style lang="less"></style>
