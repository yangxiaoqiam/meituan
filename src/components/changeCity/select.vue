<template>
   <div class="choose-wrap" @click="showWrapper" v-document-click="documentClick">
      <div class="choose">
            <span>{{value}}</span>
            <i class="el-icon-caret-bottom"></i>
            <div :class="{'mt-content':true,'active':showWrapperActive}">
                <h2>省份</h2>
                <div class="wrapper">
                    <div class="col">
                        <span class="mt-item" v-for="(item,index) in list" :key="index" >{{item}}</span>
                    </div>
                </div>
            </div>
      </div>
   </div>

</template>
<script>
    export default{
        data(){
            return{
            }
        },
        props:[
            'list',
            'value',
            'title',
            'showWrapperActive'
        ],
        methods:{
            showWrapper(e){
                e.stopPropagation();
                //this.showWrapperActive=true
                this.$emit('change_active',true)
            },
            documentClick(){
                //this.showWrapperActive=false;
                this.$emit('change_active',false)
                console.log('click')
            }
        }
    }
</script>
<style lang="scss">
        @import "@/assets/css/changecity/select.scss";
 </style>