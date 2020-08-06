<template>
  <div class="container">
    <el-card class="my-card">
      <div class="text">SecFuzz展示</div>
      <el-row :gutter="20">
        <el-col :span="8">
          <div id="scroll-board3">
            <dv-scroll-board :config="config3" />
          </div>
          <!-- <el-table :data="tableData" height="100" border style="width: 100%">
            <el-table-column prop="date" label="日期" width="100"></el-table-column>
            <el-table-column prop="name" label="姓名" width="100"></el-table-column>
            <el-table-column prop="address" label="地址"></el-table-column>
          </el-table> -->
          <div id="scroll-board2">
            <dv-scroll-board :config="config2" />
          </div>
        </el-col>
        <el-col :span="8">
          <!-- 为ECharts准备一个具备大小（宽高）的Dom -->
          <div ref="cake" style="width:600px;height:400px;"></div>
        </el-col>
        <el-col :span="8">
            <div id="scroll-board">
              <dv-scroll-board :config="config" />
            </div>
        </el-col>
      </el-row>
    </el-card>
  </div>
</template>

<script>
import echarts from 'echarts'
export default {
  name: 'ScrollBoard',
  name: 'ScrollBoard2',
  name: 'ScrollBoard3',
  data () {
    return {
      config: {
        header: ['时间', '病害信息', '数量', '标段'],
        data: [
          ['2019-07-01 19:25:00', '路面危害-松散', '5', 'xxxxxxx'],
          ['2019-07-02 17:25:00', '路面危害-路面油污清理', '13', 'xxxxxxx'],
          ['2019-07-03 16:25:00', '交安设施-交通标志牌结构', '6', 'xxxxxxx'],
          ['2019-07-04 15:25:00', '路基危害-防尘网', '2', 'xxxxxxx'],
          ['2019-07-05 14:25:00', '交安设施-交通标志牌结构', '1', 'xxxxxxx'],
          ['2019-07-06 13:25:00', '路面危害-松散', '3', 'xxxxxxx'],
          ['2019-07-07 12:25:00', '路基危害-防尘网', '4', 'xxxxxxx'],
          ['2019-07-08 11:25:00', '路面危害-路面油污清理', '2', 'xxxxxxx'],
          ['2019-07-09 10:25:00', '交安设施-交通标志牌结构', '5', 'xxxxxxx'],
          ['2019-07-10 09:25:00', '路基危害-防尘网', '3', 'xxxxxxx']
        ],
        index: true,
        columnWidth: [50, 170, 300],
        align: ['center'],
        rowNum: 7,
        headerBGC: '#1981f6',
        headerHeight: 45,
        oddRowBGC: 'rgba(0, 44, 81, 0.8)',
        evenRowBGC: 'rgba(10, 29, 50, 0.8)'
      },
      config2: {
        header: ['时间', '病害信息', '数量', '标段'],
        data: [
          ['2019-07-01 19:25:00', '路面危害-松散', '5', 'xxxxxxx'],
          ['2019-07-02 17:25:00', '路面危害-路面油污清理', '13', 'xxxxxxx'],
          ['2019-07-03 16:25:00', '交安设施-交通标志牌结构', '6', 'xxxxxxx'],
          ['2019-07-04 15:25:00', '路基危害-防尘网', '2', 'xxxxxxx'],
          ['2019-07-05 14:25:00', '交安设施-交通标志牌结构', '1', 'xxxxxxx'],
          ['2019-07-06 13:25:00', '路面危害-松散', '3', 'xxxxxxx'],
          ['2019-07-07 12:25:00', '路基危害-防尘网', '4', 'xxxxxxx'],
          ['2019-07-08 11:25:00', '路面危害-路面油污清理', '2', 'xxxxxxx'],
          ['2019-07-09 10:25:00', '交安设施-交通标志牌结构', '5', 'xxxxxxx'],
          ['2019-07-10 09:25:00', '路基危害-防尘网', '3', 'xxxxxxx']
        ],
        index: true,
        columnWidth: [50, 170, 300],
        align: ['center'],
        rowNum: 7,
        headerBGC: '#1981f6',
        headerHeight: 25,
        oddRowBGC: 'rgba(0, 44, 81, 0.8)',
        evenRowBGC: 'rgba(10, 29, 50, 0.8)'
      },
       config3: {
        header: ['时间', '病害信息', '数量', '标段'],
        data: [
          ['2019-07-01 19:25:00', '路面危害-松散', '5', 'xxxxxxx'],
          ['2019-07-02 17:25:00', '路面危害-路面油污清理', '13', 'xxxxxxx']
        ],
        index: true,
        columnWidth: [50, 170, 300],
        align: ['center'],
        rowNum: 7,
        headerBGC: '#1981f6',
        headerHeight: 45,
        oddRowBGC: 'rgba(0, 44, 81, 0.8)',
        evenRowBGC: 'rgba(10, 29, 50, 0.8)'
      }
    }
  },
  mounted () {
    this.initCake()
  },
  methods: {
    initCake () {
      const myEcharts = echarts.init(this.$refs.cake);
      const option = {
        // title: {
        //     text: '某站点用户访问来源',
        //     subtext: '纯属虚构',
        //     left: 'center'
        // },
        // tooltip: {
        //     trigger: 'item',
        //     formatter: '{a} <br/>{b} : {c} ({d}%)'
        // },
        // legend: {
        //     orient: 'vertical',
        //     left: 'left',
        //     data: ['直接访问', '邮件营销', '联盟广告', '视频广告', '搜索引擎']
        // },
        series: [
            {
                name: '访问来源',
                type: 'pie',   // 设置图表类型为饼图
                radius: '55%',  // 饼图的半径，外半径为可视区尺寸（容器高宽中较小一项）的 55% 长度。
                center: ['30%', '60%'],
                data: [
                      //数据数组，name 为数据项名称，value 为数据项值 
                    {value: 335, name: '直接访问'},
                    {value: 310, name: '邮件营销'},
                    {value: 234, name: '联盟广告'},
                    {value: 135, name: '视频广告'},
                    {value: 1548, name: '搜索引擎'}
                ],
                emphasis: {
                    itemStyle: {
                        shadowBlur: 10,
                        shadowOffsetX: 0,
                        shadowColor: 'rgba(0, 0, 0, 0.5)'
                    }
                }
            }
        ]
      };
      myEcharts.setOption(option);
    },
  },
};
</script>

<style scoped lang='less'>
.my-card {
  width: 1300px;
  height: 600px;
  background-color: rgb(111, 21, 172);
}
.text {
  text-align: center;
  font-size: 20px;
  color: #fff;
  padding-bottom: 18px;
}
.el-row {
  margin-bottom: 20px;
  &:last-child {
    margin-bottom: 0;
  }
}
.el-col {
  border-radius: 4px;
}
.bg-purple-dark {
  background: #99a9bf;
}
.bg-purple {
  background: #d3dce6;
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
#scroll-board {
  width: 100%;
  box-sizing: border-box;
  margin-left: 10px;
  height: 100%;
  // overflow: hidden;
}
#scroll-board2 {
  width: 100%;
  box-sizing: border-box;
  margin-top: 20px;
  height: 100%;
  // overflow: hidden;
}
</style>
