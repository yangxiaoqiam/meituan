<template>
<div class="page-changeCity">
    <el-row>
           <province />
    </el-row>
    <el-row></el-row>
    <el-row></el-row>
    <el-row></el-row>
</div>
</template>
<script>
    import province from '@/components/changeCity/province'
    import hot from '@/components/changeCity/hot'
    import category from '@/components/changeCity/category'
    import select from '@/components/changeCity/select'
  export default {
    components: {
        province,
        hot,
        category,
        select
    }
  }
</script>