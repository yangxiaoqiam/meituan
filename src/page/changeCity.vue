
<template>
  <div class="page-changeCity">
    <el-row>
      <province />
    </el-row>
    <el-row>
      <hot title="热门城市:" :list="hotList" />
    </el-row>
    <el-row>
      <hot title="最近访问:" :list="rencentList" />
    </el-row>
    <el-row>
      <category />
    </el-row>
  </div>
</template>
<script>
import api from "@/api/index.js";
import province from "@/components/changeCity/province";
import hot from "@/components/changeCity/hot";
import category from "@/components/changeCity/category";
import select from "@/components/changeCity/select";
export default {
  data() {
    return {
      hotList: [],
      rencentList: []
    };
  },
  created() {
    api.getHotCity().then((res) => {
      this.hotList = res.data.data;
    })
    api.getRecentCity().then((res) => {
      this.rencentList = res.data.data;

    })
  },
  components: {
    province,
    hot,
    category,
    select
  }
};
</script>
