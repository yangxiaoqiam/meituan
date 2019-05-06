
<template>
  <div class="page-changeCity">
    <el-row>
      <province/>
    </el-row>
    <el-row>
      <hot title="热门城市:" :list="hotList"/>
    </el-row>
    <el-row>
      <hot title="最近访问:" :list="rencentList"/>
    </el-row>
    <el-row>
      <category/>
    </el-row>
  </div>
</template>
<script>
import province from "@/components/changeCity/province";
import hot from "@/components/changeCity/hot";
import category from "@/components/changeCity/category";
import select from "@/components/changeCity/select";
export default {
  data() {
    return {
      hotList: ["山东", "甘肃", "安徽"],
      rencentList: ["山东1", "甘肃1", "安徽1"]
    };
  },
  components: {
    province,
    hot,
    category,
    select
  }
};
</script>
