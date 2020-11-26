<template>
  <div class="wrapper">
    <el-dialog
      title="添加用户"
      :visible.sync="dialogVisible"
      width="50%"
    >
      <div>
        <el-form :model="form" ref="ruleForm" :rules="rule" class="demo-form-inline">
          <el-form-item label="邮箱" prop="email">
            <el-input v-model="form.email" placeholder="邮箱"></el-input>
          </el-form-item>
          <el-select clearable v-model="form.accountType" prop="accountType" label="账号类型">
            <!-- <el-option label="正式" value="0"></el-option> -->
            <el-option label="模拟" value="1"></el-option>
          </el-select>
          <el-form-item label="密码" prop="pwd">
            <el-input v-model="form.pwd" placeholder="密码"></el-input>
          </el-form-item>
          <!-- <el-form-item label="金额" prop="amt">
            <el-input v-model="form.amt" placeholder="金额"></el-input>
          </el-form-item> -->
        </el-form>
        <!-- <div>
          添加的金额默认为融资资金
        </div> -->
      </div>
      <span slot="footer" class="dialog-footer">
            <el-button @click="dialogVisible = false">取 消</el-button>
            <el-button type="primary" @click="submit('ruleForm')">确 定</el-button>
        </span>
    </el-dialog>
  </div>
</template>

<script>
import * as api from '@/axios/api'

export default {
  components: {},
  props: {
    getDate: {
      type: Function,
      default: function () {

      }
    }
  },
  data () {
    return {
      dialogVisible: false,
      form: {
        email: '',
        accountType: '1',
        pwd: '',
        amt: 0
      },
      rule: {
        email: [
          { required: true, message: '请输入邮箱', trigger: 'blur' }
        ],
        accountType: [
          { required: true, message: '请选择账号类型', trigger: 'change' }
        ],
        pwd: [
          { required: true, message: '请输入密码', trigger: 'blur' }
        ],
        amt: [
          { required: true, message: '请输入金额', trigger: 'blur' }
        ]
      }
    }
  },
  watch: {},
  computed: {},
  created () {},
  mounted () {},
  methods: {
    submit (formName) {
      // 提交
      this.$refs[formName].validate(async (valid) => {
        if (valid) {
          let opts = {
            phone: this.form.email,
            accountType: this.form.accountType,
            pwd: this.form.pwd,
            amt: this.form.amt
          }
          let data = await api.addSimulatedAccount(opts)
          if (data.status === 0) {
            this.$message.success('添加成功')
            this.getDate()
          } else {
            this.$message.error(data.msg)
          }
          this.dialogVisible = false
        } else {
          return false
        }
      })
    }
  }
}
</script>
<style lang="less" scoped>
</style>
