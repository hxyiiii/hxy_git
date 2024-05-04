<template>
    <el-container direction="vertical">
        <el-header>
            <div class="title">
                <h1>从零构建Vue项目</h1>
                <h3>2252537黄熙雁 —— 4.19课堂练习</h3>
            </div>
        </el-header>
        <div class="button_input">
            <el-container direction="horizontal">
                <el-button round 
                @click="handleClick"
                size="medium">
                    {{ buttonText }}＋{{ counter }}
                </el-button>
                <el-input v-model="input" 
                    placeholder="请输入内容"
                    clearable
                    size="medium">
                </el-input> 
            </el-container>    
        </div>
        <div class="table">            
            <el-table :data="tabledata"  
            border
            stripe
            style="width: 100%">
            <el-table-column
                prop="userId"
                label="userId"
                align="center"
            ></el-table-column>
            <el-table-column
                prop="title"
                label="title"                
                align="center"
            ></el-table-column>
            <el-table-column
                prop="id"
                label="id"               
                align="center"
            ></el-table-column>
            <el-table-column
                prop="body"
                label="body"               
                align="center"
            ></el-table-column>
            </el-table>  
        </div>  
    </el-container>         
</template> 


<script>
import axios from "axios";
    export default {
        created(){
            axios({
                method:"get",
                url:"http://jsonplaceholder.typicode.com/posts",
            }).then(
                (res)=>{
                    console.log(res)
                    this.tabledata=res.data;
                }).catch(error=>{
                    console.log(error)
                })
        },
    data(){
        return{
            buttonText:'功德',
            counter: 1,
            tabledata: [],
            input: '',
        }
    },
    methods:{
        handleClick(){
            this.counter+=1;
        },
        // mounted(){
        //     this.created();
        // },
    }
    }; 
</script> 

<style>
    .el-header{
        line-height: 20px;
        margin-bottom: 20px;
    }
    .el-container{
        margin-block: 40px;
    }
    .button_input{
        margin:auto;
        justify-self:center;
        width: 600px;
    }
    .el-button{
        margin-right:20px;
        height:max-content;
        width:max-content;
        background-color: rgb(230, 230, 222);
    }
    .el-inpupt__inner{
        border-color: #333;
        border-radius: 100px;
        box-shadow: 0 0 0 2px rgba(64, 158, 255, 0.2);
        background-color: #7e90ab;
    }
    .el-input:hover .el-input__inner {
        border-color: #aeb5c1;
    }
    .table{
        margin-inline:100px;
    }
    .el-table {
        font-family: Arial, sans-serif; 
        color: #333; 
    }
    .el-table th,
    .el-table td {
        padding: 12px; 
        border: 1px solid #ebeef5;
        border-radius: 5px; 
    }
    .el-table th {
        background-color: #f5f7fa00; 
        font-weight: bold; 
    }
</style>    