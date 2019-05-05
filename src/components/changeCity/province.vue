<template>
    <div>
      <span class="name">按省份选择:</span> 
      <m-select :list='provinceList' :value="province" title="省份" :showWrapperActive="provinceActive"  @change_active="changeProvinceActive"/>
      <m-select :list='cityList' :value="city" title="城市" :showWrapperActive="cityActive"  @change_active="changeCityActive"/>
      <span>直接搜索</span>
      <el-select v-model="searchWord" filterable remote reserve-keyword placeholder="请输入关键词" :loading="loading" :remote-method="remoteMethod">  
          <el-option v-for="item in searchList" :key="item" :label="item" :value="item"></el-option>
        </el-select>
    </div>
    </template>
    <script>
        import MSelect from '@/components/changeCity/select'
      
      export default {
        data(){
          return{
            provinceList:['山东','甘肃','安徽'],
            province:'省份',
            cityList:['阜阳','黄山'],
            city:'城市',
            provinceActive:false,
            cityActive:false,
            searchList:['山东','甘肃','安徽'],
            searchWord:'',
            loading:false

          }
        },
        components: {
          MSelect
        },
        methods:{
         
          changeProvinceActive(flag){
            this.provinceActive=flag
            if (flag) {
              this.cityActive = false;
            }
          },
          changeCityActive(flag){
            this.cityActive=flag;
            if (flag) {
              this.provinceActive = false;
            }
          },
          remoteMethod(val){

          }
        }
      }
    </script>
    <style lang="scss">
        @import "@/assets/css/changecity/iselect.scss";
 </style>