<template>
<div class="wrapper">
  <el-form :model="rform" :rules="rules" ref="rform">
    <el-form-item  prop="email">
      <el-input v-model="rform.email" prefix-icon="fa fa-envelope-o" placeholder="Email"></el-input>
    </el-form-item>
    <el-form-item  prop="password">
      <el-input v-model="rform.password" prefix-icon="fa fa-key" placeholder="Password"></el-input>
    </el-form-item>
    <el-form-item>
      <el-button class="w-button" @click="submitForm('rform')"> Login </el-button>
    </el-form-item>
    <el-form-item>
      <el-button class="w-button" @click="registerForm()"> Register </el-button>
    </el-form-item>
  </el-form>
  <el-dialog title="注册账户" :visible.sync="dialogVisible" width="25%">
    <el-form :model="registerF">
      <el-form-item label="Name" :label-width="'80px'">
        <el-input v-model="registerF.name" placeholder="Taylor Swift"></el-input>
      </el-form-item>
      <el-form-item label="E-Mail" :label-width="'80px'">
        <el-input v-model="registerF.email" placeholder="Taylor@Swift.com"></el-input>
      </el-form-item>
      <el-form-item label="Password" :label-width="'80px'">
        <el-input v-model="registerF.password"></el-input>
      </el-form-item>
      <el-form-item :label-width="'80px'">
        <el-button class="w-button">Create a account</el-button>
      </el-form-item>
    </el-form>
  </el-dialog>
</div>

</template>

<script>
export default {
  name: 'Login',
  data () {
    return {
      dialogVisible: false,
      rform: {
        email: '',
        password: ''
      },
      registerF: {
        name: '',
        email: '',
        password: ''
      },
      rules: {
        email: [{ required: true, message: '请输入邮箱' }],
        password: [{ required: true, message: '请输入密码' }]
      }
    }
  },
  methods: {
    submitForm (formName) {
      this.$refs[formName].validate((valid) => {
        if (valid) {
          this.$router.push('/home')
        } else {
          console.log('error submit!!')
          return false
        }
      })
    },
    registerForm () {
      this.dialogVisible = true
    }
  }
}
</script>

<style lang="stylus" scoped rel="stylesheet/stylus">
.wrapper {
  width: 345px;
  margin: 10% auto;

  .w-button {
    width: 100%;
    background-color: #000;
    color: #fff;

    &:hover {
      background-color: #5f5d5d;
    }
  }
}
</style>
