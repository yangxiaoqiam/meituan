<template>
  <div class="m-products-list">
    <ul>
      <li v-for="item in nav" :key="item.key" :class="{'s-nav-active': item.active}">{{item.name}}</li>
    </ul>
    <el-row>
      <item v-for="(item, index) in productList" :key="index" :meta="item" />
    </el-row>
  </div>
</template>
<script>
import Item from './item.vue'
import api from '@/api/index.js'
export default {
  data() {
    return {
      nav: [
        {
          key: "s-default",
          name: "智能排序",
          active: true
        },
        {
          key: "s-price",
          name: "价格最低",
          active: false
        },
        {
          key: "s-score",
          name: "人气最高",
          active: false
        },
        {
          key: "s-comment",
          name: "评价最高",
          active: false
        }
      ],
      productList: [{
        "image": "p1.meituan.net/travel/d20079b903b559fe8ea5a5eb8fb99a12483467.png@220w_125h_1e_1c",
        "title": '火锅老店',
        "type": "food",
        "score": "2.5",
        "commentNum": 0,
        "comment": [{
          "username": 'ccc',
          "evalaute": "好吃"
        }]
      }, {
        "image": "p1.meituan.net/travel/d20079b903b559fe8ea5a5eb8fb99a12483467.png@220w_125h_1e_1c",
        "title": '奶茶店',
        "type": "tea",
        "score": "5",
        "commentNum": 0,
        "comment": [{
          "username": 'ccc',
          "evalaute": "好吃"
        }]
      }]
    };
  },
  created() {
    api.getProductsList().then(res => {
      this.productList = res.data.data;
    })
  },
  components: {
    Item
  }
};
</script>

