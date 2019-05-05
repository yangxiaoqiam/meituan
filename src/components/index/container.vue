<template>
  <div class="m-istyle">
    <dl @mouseover="over">
      <dt>{{nav.title}}</dt>
      <dd v-for="(item,index) in nav.list" :key="index" :class="{active:kind==item.tab}" :data-type="item.tab">{{item.text}}</dd>
    </dl>

    <ul class="ibody">
      <li v-for="(item,index) in list" :key="index">
        <el-card :body-style="{ padding: '0px' }" shadow="never">
          <img :src="item.image" class="image">
          <div  class="cbody">
            <div class="title" :title="item.title">{{item.title}}</div>
            <div class="sub-title" :title="item.sub_title">{{ item.sub_title}}
            </div>
            <div class="price-info">
              <span class="current-price-wrapper">
                <span class="price-symbol numfont">¥</span>
                <span class="current-price numfont">{{item.price_info.current_price}}</span>
              </span>
              <span class="old-price">门市价{{item.price_info.old_price}}</span>
              <span class="sold bottom-right-info">{{item.address}}</span>
            </div>
            </div>
        </el-card>
      </li>

    </ul>
  </div>
</template>
<script>
  export default {
    props: ["nav"],
    data(){
     return{
      kind:'all',
        list:[{
          image:"//p0.meituan.net/poi/c2b482474377fc31a8311f46055f40b0442616.png@368w_208h_1e_1c",
          title:"金泉港IMAX国际影城",
          sub_title:"免押金,可停车,有情侣座,儿童票,有WIFI,IMAX厅,杜比全景声厅",
          price_info:{
            current_price:'12',
            old_price:'20'
          },
          address:'地址地址地址'
        },{
          image:"//p0.meituan.net/poi/c2b482474377fc31a8311f46055f40b0442616.png@368w_208h_1e_1c",
          title:"金泉港IMAX国际影城",
          sub_title:"22",
          price_info:{
            current_price:'30',
            old_price:'20'
          },
          address:'地址2'
        },{
          image:"//p0.meituan.net/poi/c2b482474377fc31a8311f46055f40b0442616.png@368w_208h_1e_1c",
          title:"金泉港IMAX国际影城",
          sub_title:"22",
          price_info:{
            current_price:'30',
            old_price:'20'
          },
          address:'地址2'
        },{
          image:"//p0.meituan.net/poi/c2b482474377fc31a8311f46055f40b0442616.png@368w_208h_1e_1c",
          title:"金泉港IMAX国际影城",
          sub_title:"22",
          price_info:{
            current_price:'30',
            old_price:'20'
          },
          address:'地址2'
        }]
     }
    },
    methods: {
      over(e){
      
        let dom=e.target;
        let tagName=dom.tagName.toLowerCase();
        if(tagName !='dd'){
          return false
        }
        this.kind=dom.getAttribute('data-type')
        console.log(e)
      }
    }
  }

</script>
<style lang="scss">
  @import "@/assets/css/index/artistic.scss";

</style>
