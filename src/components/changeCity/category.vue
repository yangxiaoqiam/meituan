<template>
  <div class="category">
    <dl class="m-categroy">
      <dt>按拼音首字母选择：</dt>
      <dd v-for="(item,index) in list" :key="index">
        <a :href="'#city-'+item">{{item}}</a>
      </dd>
    </dl>
    <dl class="m-categroy-section" v-for="(item,index) in cityGroup" :key="index" :id="'city-'+index">
      <dt>{{index}}</dt>
      <dd>
        <span v-for="city in item" :key="city.id">{{city.name}}</span>
      </dd>
    </dl>
  </div>
</template>
<script>
import api from "@/api/index.js";
export default {
  data() {
    return {
      list: "ABCDEFGHIJKLMNOPQRSTUVWXYZ".split(""),
      cityList: [],
      cityGroup: {}
    };
  },
  created() {
    var data = [
      {
        id: 60,
        name: "青岛",
        pinyin: "qingdao",
        acronym: "qd",
        rank: "B",
        firstChar: "Q"
      },
      {
        id: 81,
        name: "淄博",
        pinyin: "zibo",
        acronym: "zb",
        rank: "C",
        firstChar: "Z"
      },
      {
        id: 96,
        name: "济南",
        pinyin: "jinan",
        acronym: "jn",
        rank: "B",
        firstChar: "J"
      },
      {
        id: 104,
        name: "烟台",
        pinyin: "yantai",
        acronym: "yt",
        rank: "C",
        firstChar: "Y"
      },
      {
        id: 222,
        name: "枣庄",
        pinyin: "zaozhuang",
        acronym: "zaozhuang",
        rank: "D",
        firstChar: "Z"
      },
      {
        id: 223,
        name: "东营",
        pinyin: "dongying",
        acronym: "dy",
        rank: "D",
        firstChar: "D"
      },
      {
        id: 224,
        name: "潍坊",
        pinyin: "weifang",
        acronym: "wf",
        rank: "C",
        firstChar: "W"
      },
      {
        id: 225,
        name: "济宁",
        pinyin: "jining",
        acronym: "jining",
        rank: "C",
        firstChar: "J"
      },
      {
        id: 226,
        name: "泰安",
        pinyin: "taian",
        acronym: "ta",
        rank: "D",
        firstChar: "T"
      },
      {
        id: 227,
        name: "威海",
        pinyin: "weihai",
        acronym: "weihai",
        rank: "C",
        firstChar: "W"
      },
      {
        id: 228,
        name: "日照",
        pinyin: "rizhao",
        acronym: "rizhao",
        rank: "D",
        firstChar: "R"
      },
      {
        id: 229,
        name: "莱芜",
        pinyin: "laiwu",
        acronym: "lw",
        rank: "E",
        firstChar: "L"
      },
      {
        id: 230,
        name: "临沂",
        pinyin: "linyi",
        acronym: "linyi",
        rank: "C",
        firstChar: "L"
      },
      {
        id: 231,
        name: "德州",
        pinyin: "dezhou",
        acronym: "dz",
        rank: "D",
        firstChar: "D"
      },
      {
        id: 232,
        name: "聊城",
        pinyin: "liaocheng",
        acronym: "lc",
        rank: "D",
        firstChar: "L"
      },
      {
        id: 233,
        name: "滨州",
        pinyin: "binzhou",
        acronym: "bz",
        rank: "D",
        firstChar: "B"
      },
      {
        id: 234,
        name: "菏泽",
        pinyin: "heze",
        acronym: "heze",
        rank: "D",
        firstChar: "H"
      },
      {
        id: 453,
        name: "兖州",
        pinyin: "yanzhou",
        acronym: "yanzhou",
        rank: "E",
        firstChar: "Y"
      }
    ];
    var obj = {};
    data.forEach((item, index) => {
      if (!obj[item.firstChar.toUpperCase()]) {
        obj[item.firstChar.toUpperCase()] = [];
      }
      obj[item.firstChar.toUpperCase()].push(item);
    });
    this.cityGroup = obj;
    console.log(this.cityGroup);
  },
  methods: {}
};
</script>

<style lang="scss">
@import "@/assets/css/changecity/categroy.scss";
</style>
