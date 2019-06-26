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
  props: ['id'],
  name: 'UserProfile',
  beforeRouteEnter: (to, from, next) => {
    console.log('准备进入个人信息页')
    // 注意，一定要在 next 中请求，因为该方法调用时 Vue 实例还没有创建，此时无法获取到 this 对象(即这里不能直接调getData方法)，
    // 在这里使用官方提供的回调函数拿到当前实例
    next(vm => {
      vm.getData()
    })
  },
  beforeRouteLeave: (to, from, next) => {
    console.log('准备离开个人信息页')
    next()
  },
  methods: {
    getData: function () {
      this.axios({
        method: 'get',
        url: 'http://localhost:8080/data.json'
      }).then(function (repos) {
        console.log(repos)
      }).catch(function (error) {
        console.log(error)
      })
    }
  }
}
