<template>
    <div class="category">
        <dl class="m-categroy">
            <dt>按拼音首字母选择：</dt>
            <dd v-for="(item,index) in list"><a :href="'#city-'+item">{{item}}</a></dd>
        </dl>
       
    </div>
</template>
<script>
import api from '@/api/index.js'
export default {
    data() {
        return {
            list: 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'.split(''),
            cityList: [],
            cityGroup: {},
        }
    },
    created() {
    

    },
    methods: {
        
    }
}
</script>

<style lang="scss">
    @import "@/assets/css/changecity/categroy.scss";
</style>

