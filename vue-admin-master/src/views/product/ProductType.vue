<template>
    <dev>
        <el-tree :data="productTypes" :props="defaultProps" @node-click="handleNodeClick"></el-tree>
    </dev>
</template>

<script>
    export default {
        data(){
            return {
                productTypes:[],
                defaultProps: {
                    children: 'children',
                    label: 'name'
                }
            }
        },
        methods:{
            //加载树的数据
            loadTreeData(){
                this.$http.get("/product/productType/tree").then((res)=>{
                    this.productTypes = res.data;
                })
            }
        },
        mounted(){
            this.loadTreeData();
        }
    }
</script>

<style scoped>
    .el-aside{
        border:1px solid #ccc;
        border-right: none;
    }
    .el-main{
        border:1px solid #ccc;
    }
</style>