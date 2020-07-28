<template>
  <div class="container">
    <el-card>
      <div slot="header">迭代测试-ICSL测试前</div>
      <el-row>
        <el-col :span="24">
          <div class="grid-content bg-purple-dark">漏洞基本信息</div>
          </el-col>
      </el-row>
      <el-form label-width="130px">
        <el-row :gutter="24">
          <el-col :span="8">
            <el-form-item label="请输入：">
              <el-input style="width:200px"></el-input>
            </el-form-item>
          </el-col>
          <el-col :span="8">
            <el-form-item label="请输入：">
              <el-input style="width:200px"></el-input>
            </el-form-item>
          </el-col>
          <el-col :span="8">
            <el-form-item label="请输入：">
              <el-input style="width:200px"></el-input>
            </el-form-item>
          </el-col>
          <el-col :span="8">
            <el-form-item  label=" 请输入：" class="demo-input-suffix">
              <!-- <el-input
                placeholder="请选择日期"
                suffix-icon="el-icon-date"
                style="width:200px"
                v-model="input1">
              </el-input> -->
              <el-date-picker
                v-model="value1"
                type="date"
                placeholder="选择日期">
              </el-date-picker>
            </el-form-item>
          </el-col>
          <el-col :span="8">
            <el-form-item label="请输入：">
              <el-input
                placeholder="请选择负责人"
                prefix-icon="el-icon-user"
                style="width:200px"
                v-model="input2">
              </el-input>
            </el-form-item>
          </el-col>
        </el-row>
      </el-form>
      <el-form>
        <el-form-item label="问题澄清：">
          <!-- <el-button placeholder="操作日志" style="width:500px">
          </el-button> -->
        </el-form-item>
        <el-form-item class="cz"> 操作日志 </el-form-item>
      </el-form>
      <el-form>
        <el-form-item label="审批" prefix-icon="el-icon-s-check">
          <!-- <el-input prefix-icon="el-icon-s-check"></el-input> -->
        </el-form-item>
      </el-form>
      <el-form label-width="80px" size="small">
        <el-form-item label="审批结果">
          <el-radio-group v-model="radio">
            <el-radio :label="3">同意</el-radio>
            <el-radio :label="6">驳回</el-radio>
          </el-radio-group>
        </el-form-item>
      </el-form>
      <el-form label-width="80px" size="small">
        <el-form-item label="转审意见">
          <el-input
          type="textarea"
          :rows="2"
          v-model="textarea"
          style="width:500px"
          >
        </el-input>
        </el-form-item>
        <el-form-item label-width="200px">
          <el-button type="primary" style="">取消</el-button>
          <el-button type="primary">提交</el-button>
        </el-form-item>
      </el-form>
    </el-card>
  </div>
</template>

<script>
export default {
  data () {
    return {
      input2: '',
      input3: '',
      input4: '',
      textarea: '',
      radio: 3,
      value1: '',
      value2: '',
      pickerOptions: {
        disabledDate (time) {
          return time.getTime() > Date.now()
        },
        shortcuts: [{
          text: '今天',
          onClick (picker) {
            picker.$emit('pick', new Date())
          }
        }, {
          text: '昨天',
          onClick (picker) {
            const date = new Date()
            date.setTime(date.getTime() - 3600 * 1000 * 24)
            picker.$emit('pick', date)
          }
        }, {
          text: '一周前',
          onClick (picker) {
            const date = new Date()
            date.setTime(date.getTime() - 3600 * 1000 * 24 * 7)
            picker.$emit('pick', date)
          }
        }]
      }
    }
  }
}
</script>

<style scoped lang='less'>
.el-row {
    margin-bottom:10px;
    border-bottom: 1px;
    }
  .el-col {
    border-radius: 1px;
  }
.el-card {
  margin-bottom: 20px;
}
.cz {
  width: 800px;
  margin: 0 auto;
  padding-bottom: 10px;
  font-size: 20px;
  line-height: 32px;
  height: 30px;
  border-radius: 3px;
  border:1px solid #ccc;
  text-align: center;
}
</style>
