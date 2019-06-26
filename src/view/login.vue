<template>
  <div>
    <el-form ref="loginForm" :model="loginForm" :rules="rules">
      <el-form-item label="账号" prop="username">
        <el-input type="text" placeholder="请输入账号" v-model="loginForm.username"></el-input>
      </el-form-item>

      <el-form-item label="密码" prop="password">
        <el-input type="password" placeholder="请输入密码" v-model="loginForm.password"></el-input>
      </el-form-item>

      <el-form-item>
        <el-button type="primary" @click="commitForm('loginForm')">登录</el-button>
      </el-form-item>

    </el-form>
  </div>
</template>

<script>

export default {
  name: 'login',
  data () {
    return {
      loginForm: {
        username: '223',
        password: '22'
      },
      rules: {
        username: [
          {required: true, message: '账号不能为空', trigger: 'blur'}
        ],
        password: [
          {required: true, message: '密码不可为空', trigger: 'blur'}
        ]
      }
    }
  },
  methods: {
    commitForm (form) {
      alert(form)
      alert('username:' + this.loginForm.username + 'password:' + this.loginForm.password)
      alert('rules:' + this.rules.username)
      // alert('这是一条消息提示')
      // 为表单绑定验证功能
      this.$refs[form].validate((valid) => {
        if (valid) {
          // 使用 vue-router 路由到指定页面，该方式称之为编程式导航
          // this.$router.push("/main")
          alert('这是一条消息提示')
        } else {
          this.dialogVisible = true
          return false
        }
      })
    }
  }
}
</script>

<style scoped>

</style>
