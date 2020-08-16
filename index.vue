<template>
    <div class="container">
        <div class="map">
            <div class="quan quan_1"></div>
            <div class="quan quan_2"></div>
            <div class="quan quan_3"></div>
            <div class="quan1 quan_1"></div>
            <div class="quan1 quan_2"></div>
            <div class="quan1 quan_3"></div>
            <div class="quan2 quan_1"></div>
            <div class="quan2 quan_2"></div>
            <div class="quan2 quan_3"></div>
            <div class="quan3 quan_1"></div>
            <div class="quan3 quan_2"></div>
            <div class="quan3 quan_3"></div>
            <div class="quan4 quan_1"></div>
            <div class="quan4 quan_2"></div>
            <div class="quan4 quan_3"></div>
            <div>
                <div class="title" style="font-size:30px;color:white;">应用威胁检测全网安全态势</div>
                <el-row>
                    <el-col :span="4">
                        <div class="table" style="font-size:15px">20XX.XX.XX AI检测TOP30恶意应用
                            <el-table
                                :data="shiyanshidata"
                                :row-style="{height:'20px'}"
                                :cell-style="{padding:'0px'}"
                                style="font-size:10px"
                            >
                                <el-table-column
                                    type="index"
                                    :index="indexMethod"
                                    label="排名"
                                >
                                </el-table-column>

                                <el-table-column
                                    label="应用名称"
                                    prop="appname"
                                    width="100px"
                                    align="center"
                                >
                                </el-table-column>

                                <el-table-column
                                    label="应用数量"
                                    prop="quantity"
                                    width="100px"
                                    align="center"
                                >
                                </el-table-column>
                            </el-table>
                        </div>
                   </el-col>
                   <el-col :span="16">
                       <div class="grid-content bg-purple"></div>
                   </el-col>
                   <el-col :span="4" style="text-align:right">
                       <div class="table" style="font-size:15px">20XX.XX.XX恶意威胁种类排名
                           <el-table
                                :data="youshangjiaodata"
                                :row-style="{height:'20px'}"
                                :cell-style="{padding:'0px'}"
                                style="font-size:10px"
                            >
                                <el-table-column
                                    type="index"
                                    :index="indexMethod"
                                >
                                </el-table-column>

                                <el-table-column
                                    label="恶意种类"
                                    prop="malicioustype"
                                    width="100px"
                                    align="center"
                                >
                                </el-table-column>

                                <el-table-column
                                    label="检出应用数"
                                    prop="quantity"
                                    width="100px"
                                    align="center"
                                >
                                </el-table-column>
                            </el-table>
                       </div>
                   </el-col>
                </el-row>
                <div class="scroll-board">
                    <div style="font-size:16px;margin-top:-10px;">威胁日志</div>
                    <dv-scroll-board :config="config" />
                </div>
            </div>
        </div>
    </div>
</template>

<script>
// import {
//     AppRankingInfo,
//     MaliciousThreatsInfo,
//     ThreatLogInfo
// } from "../../services/laboratory_services";
// import map from "./map";

export default {
    name: "Laboratory",
    // components: {
    //     map
    // },
    props:{},
    data() {
        return {
            shiyanshidata:[],
            youshangjiaodata:[],
            youxiajiaodata:[],
            config: {}
        };
    },
    computed: {},
    watch: {},
    created() {
        // this.AppRanking(),
        // this.MaliciousThreat(),
        // this.youshangjiaodataInfo()
    },
    mounted() {},
    methods: {
        AppRanking() {
            AppRankingInfo().then(res => {
                if (!res.datas.code === 0){
                    throw new Error(res.datas.msg);
                }
                else {
                    this.shiyanshidata = res.datas.list;
                }
            });
        },

        MaliciousThreat() {
            MaliciousThreatsInfo().then(res => {
                if (!res.datas.code === 0){
                    throw new Error(res.datas.msg);
                }
                else {
                    this.youshangjiaodata = res.datas.list;
                }
            });
        },

        youshangjiaodataInfo() {
            ThreatLogInfo().then(res => {
                if (!res.datas.code === 0){
                    throw new Error(res.datas.msg);
                }
                else {
                    this.youxiajiaodata = res.datas.list;
                    let array = [];
                    this.youxiajiaodata.forEach((item, index) => {
                        let arr1 = Object.values(item);
                        let arr2 = arr1.splice(0,6);
                        array.push(arr2);
                    });
                    // console.log(array);
                    // console.log(this.config.data);
                    this.config = {
                        header: [
                            "a",
                            "a",
                            "a",
                            "a",
                            "a",
                            "a",
                        ],
                        data: array,
                        index: false,
                        columnWidth: [220, 200, 160, 100, 150, 120],
                        align: ["center"],
                        rowNum: 7,
                        headerBGC: "#1981f6",
                        headerHeight: 20,
                        oddRowBGC: "rgba(0, 44, 81, 0.8)",
                        evenRowBGC: "rgba(10, 29, 50, 0.8)"
                    }
                }
            });
        }
    }
};
</script>

<style lang="less" scoped>
    .title {
        background: "#5b9bd5";
        font-size: 10px;
        width: 700px;
        height: 40px;
        text-align: center;
        margin: 0 auto;
    }

    .table {
        text-align: center;
        font-weight: 700;
    }

    .el-table::before {
        left: 0;
        bottom :0;
        width: 100%;
        height: 0px;
    }

    .el-table {
        color: black;
    }

    .table /deep/ .el-table--fit {
        padding: 20px;
    }

    .table /deep/ .el-table, .el-table__expanded-cell {
        background-color:transparent;
    }

    .table /deep/ .el-table tr {
        background-color:transparent !important;
    }

    .table /deep/ .el-table--enabke--row-transition .el-table__body td, .el-table .cell {
        background-color: transparent;
    }

    .el-row {
        margin-bottom:20px;
    }

    .el-row :last-child {
        margin-bottom:0;
    }

    .el-col {
        border-radius: 4px;
    }

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
    
    .scroll-board {
        position: absolute;
        right: 0;
        top: 500px;
        width: 40%;
        box-sizing: border-box;
        margin-left: 20px;
        height: 400px;
        overflow: hidden;
    }

    .map {
        width: 100%;
        height: 900px;
        background: url("../../assets/images/map.png") no-repeat center/cover;
    }

    img {
        width: 100%;
        height: 100%;
    }

    @keyframes fangda {
      75% {
        width:5px;
        height: 5px;
        // transform: translate(-50%, -50%) scale(1);
        transform:  translate(0) scale(1);
        opacity: 0;
      }
      100% {
        width: 5px;
        height: 5px;
        // transform: translate(-50%, -50%) scale(4);
        transform:  translate(100) scale(2);
        opacity: 1;
      }
    }
    .quan {
      width: 5px;
      height: 5px;
      background: red;
      box-shadow: 0 0 5px red;
      border-radius: 50%;
      position: absolute;
      top: 50%;
      left: 90%;
      // transform: translate(-50%, -50%);
      /* 调用 */
      animation: fangda 3s linear infinite;
      animation-delay: 1.4s;
    }

    .quan1 {
      width: 5px;
      height: 5px;
      background: black;
      /* border: 1px solid yellow; */
      box-shadow: 0 0 5px black;
      border-radius: 50%;
      position: absolute;
      top: 30%;
      left: 30%;
      // transform: translate(-50%, -50%);
      animation: fangda 3s linear infinite;
       animation-delay: 2.8s;
    }

    .quan2 {
      width: 5px;
      height: 5px;
      background: yellow;
      box-shadow: 0 0 5px yellow;
      border-radius: 50%;
      position: absolute;
      top: 30%;
      left: 70%;
      // transform: translate(-50%, -50%);
      animation: fangda 3s linear infinite;
    }

    .quan3 {
      width: 5px;
      height: 5px;
      background: blue;
      box-shadow: 0 0 5px blue;
      border-radius: 50%;
      position: absolute;
      top: 60%;
      left: 30%;
      // transform: translate(-50%, -50%);
      animation: fangda 3s linear infinite;
       animation-delay: 5.2s;
    }
    
    .quan4 {
        width: 5px;
        height: 5px;
        background: pink;
        box-shadow: 0 0 5px pink;
        border-radius: 50%;
        position: absolute;
        top: 90%;
        left: 60%;
        // transform: translate(-50%, -50%);
        animation: fangda 3s linear infinite;
         animation-delay: 6.6s;
    }

</style>
