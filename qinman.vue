<template>
<div class="container">
    <div id="qinman">
        <div class="title">yin gyiondsgfiushfgikshfn</div>
        <!-- <el-row :gutter="20"> -->
            <!-- <el-col :span="4"> -->
                <div  class="rightTop">
                    <h2>右上角那个表的名字亲曼桑</h2>
                    <el-table
                        :data="youshangjiaodata"
                        stripe
                    >
                        <el-table-column
                            type="index"
                            :index="indexMethod"
                        >
                        </el-table-column>
                        <el-table-column label="隐私窃取" prop="qiequ" width="100px"  align="center"></el-table-column>
                        <el-table-column label="数量" prop="num" width="100px" align="center"></el-table-column>
                        <el-table-column label="zhiliang" prop="num" width="100px" align="center"></el-table-column>
                    </el-table>
                </div>  
            <!-- </el-col> -->
            <!-- <el-col :span="16"><div class="grid-content bg-purple"></div></el-col> -->
            <!-- <el-col :span="4" style="text-align:right"> -->
                <div  class="leftTop">
                    <h2>左上角那个表的名字亲曼桑</h2>
                    <el-table
                        :data="youshangjiaodata"
                        stripe
                    >
                        <el-table-column
                            type="index"
                            :index="indexMethod"
                        >
                        </el-table-column>
                        <el-table-column label="隐私窃取" prop="qiequ" width="100px"  align="center"></el-table-column>
                        <el-table-column label="数量" prop="num" width="100px" align="center"></el-table-column>
                    </el-table>
                </div>
            <!-- </el-col> -->
        <!-- </el-row> -->
        <div class="rightBottom">
        <div id="scroll-board"> 
            <dv-scroll-board :config="config" style="width:500px;height:300px; text-align:center" />
        </div>
    </div>
    </div>
</div>
</template>

<script>
// import {
//     MaliciousThreats
// } from "../../services/qinman_services"
// import { Loading } from "element-ui"
export default {
    name: 'ScrollBoard',
    data() {
        return {
            config:{
                // header: ['威胁日志'],
                header:['攻击者地区', '攻击者IP', '端口','被攻击地区','攻击类型'],
                data: [
                        ['', '', '','','']
                        // ['CN', '183.195.*113', '445','CN','DDOS'],
                        // ['行3列1', '行3列2', '行3列3','行2列4','行2列4'],
                        // ['行4列1', '行4列2', '行4列3','行2列4','行2列4'],
                        // ['行5列1', '行5列2', '行5列3','行2列4','行2列4'],
                        // ['行6列1', '行6列2', '行6列3','行2列4','行2列4'],
                        // ['行7列1', '行7列2', '行7列3','行2列4','行2列4'],
                        // ['行8列1', '行8列2', '行8列3','行2列4','行2列4'],
                        // ['行9列1', '行9列2', '行9列3','行2列4','行2列4'],
                        // ['行10列1', '行10列2', '行10列3','行2列4','行2列4']
                ],
                index: true,
                columnWidth: [40, 100, 100,90,110,100],
                align: ['center'],
                rowNum: 7,
                headerBGC: '#1981f6',
                headerHeight: 45,
                oddRowBGC: 'rgba(0, 44, 81, 0.8)',
                evenRowBGC: 'rgba(10, 29, 50, 0.8)'
            },
            youshangjiaodata:[
                {
                    qiequ: "隐私窃取",
                    num: "10"
                },
                {
                    qiequ: "数据窃取",
                    num: "1"
                },
                {
                    qiequ: "信息窃取",
                    num: "20"
                },
                {
                    qiequ: "文件窃取",
                    num: "20"
                },
                {
                    qiequ: "问题窃取",
                    num: "20"
                },
                {
                    qiequ: "隐私窃取",
                    num: "10"
                },
                {
                    qiequ: "隐私窃取",
                    num: "10"
                },
                {
                    qiequ: "隐私窃取",
                    num: "10"
                },
                {
                    qiequ: "隐私窃取",
                    num: "10"
                },
                {
                    qiequ: "隐私窃取",
                    num: "10"
                }
                ]
        };
    },

    created() {
        this.rightdata()
    },
    methods: {
        rightdata() {
            MaliciousThreats().then(res=>{
                if(!res.datas.code === 0){
                    throw new Error(res.datas.msg);
                }
                if(res.datas.code === 0){
                    this.youshangjiaodata = res.datas.list;
                }
            })
        },
        bottomData() {
            MaliciousThreats().then(res=>{
                if(!res.datas.code === 0){
                    throw new Error(res.datas.msg);
                }
                if(res.datas.code === 0){
                    this.youxaijiaodata = res.datas.list;
                    console.log(this.youxaijiaodata)
                    data = this.youxaijiaodata;
                    console.log(data)
                }
            })
        }
        
    }
}
</script>

<style scoped>
#scroll-board {
  width: 100%;
  box-sizing: border-box;
  margin-left: 20px;
  height: 100%;
  overflow: hidden;
}
#qinman{
    width: 100%;
    height: 100%;
    /* position: relative; */
}
.title{
    text-align:center;
    border:1px solid #000;
}

.rightTop{
    width: 400px;
    height: 300px;
    top:0%;
    left:2%;
    position: absolute;
}
.leftTop{
    width: 300px;
    height: 200px;
    top:0%;
    right:2%;
    position: absolute;
}
.rightBottom{
    width: 500px;
    height: 500px;
    top:100%;
    right:2%;
    position: absolute;
}


.el-row {
    margin-bottom: 20px;
  }
   .el-row last-child {
      margin-bottom: 0;
    }
  .el-col {
    border-radius: 4px;
  }
  /* .bg-purple-dark {
    background: #99a9bf;
  }
  .bg-purple {
    background: #d3dce6;
  } */
  .bg-purple-light {
    background: #e5e9f2;
  }
  .grid-content {
    border-radius: 4px;
    min-height: 36px;
  }
  .row-bg {
    padding: 10px 0;
    background-color: #f9fafc;
  }
</style>
