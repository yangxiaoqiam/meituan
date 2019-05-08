<template>
  <div class="page-register">
    <div class="header">
      <header>
        <a href="#" class="site-logo"></a>
        <div class="login">
          <span>已有美团账号</span>
          <router-link :to="{name: 'login'}">登录</router-link>
        </div>
      </header>
    </div>
    <div class="content">
      <el-form :model="registerForm" status-icon :rules="rules" ref="registerForm" label-width="100px" class="demo-ruleForm">
        <el-form-item label="用户名" prop="userName">
          <el-input type="test" v-model="registerForm.userName" autocomplete="off">></el-input>
        </el-form-item>
        <el-form-item label="密码" prop="password">
          <el-input type="password" v-model="registerForm.password" @input="input"></el-input>
          <div class="pw-strength">
            <div :class="['bar',strengthClass]"></div>
            <div class="letter">
              <span>弱</span>
              <span>中</span>
              <span>强</span>
            </div>
          </div>
        </el-form-item>
        <el-form-item label="确认密码" prop="rePassword">
          <el-input v-model="registerForm.rePassword"></el-input>
        </el-form-item>
        <el-form-item label="确认密码">
          <el-button type="primary" @click="submitForm('registerForm')">提交</el-button>
        </el-form-item>
      </el-form>
    </div>
    <footer></footer>
  </div>
</template>

<script>
import api from '@/api/index.js'
export default {

  data() {
    var validateUser = (rule, value, callback) => {
      if (value === "") {
        callback(new Error('请输入用户名'));
      } else if (value.length < 4 || value.length > 16) {
        callback(new Error('用户名必须为4-16位的字母数字下划线组成!'));
      } else {
        callback();
      }
    };
    var validatePass = (rule, value, callback) => {
      if (value === "") {
        callback(new Error('请输入密码'));
      } else {
        if (this.registerForm.password !== '') {
          this.$refs.registerForm.validateField('password');
        }
        callback();
      }
    };
    var validatePass2 = (rule, value, callback) => {
      if (value === " ") {
        callback(new Error('请再次输入密码'));
      } else if (value !== this.registerForm.rePassword) {
        callback(new Error('两次输入密码不一致!'));
      } else {
        callback();
      }
    };
    return {
      registerForm: {
        userName: '',
        password: '',
        rePassword: '',
        strengthClass: ''
      },
      strengthClass: "",
      rules: {
        userName: [{ validator: validateUser, trigger: "blur" }],
        pass: [{ validator: validatePass, trigger: "blur" }],
        rePassword: [{ validator: validatePass2, trigger: "blur" }]
      }
    }
  },
  methods: {
    submitForm(formName) {
      this.$refs[formName].validate((valid) => {
        if (valid) {
          api.register({
            params: this.registerForm
          }).then((res) => {
            if (res.data.status == "success") {
              this.$router.push({ name: 'login' });
            } else {
              alert(res.data.msg)
            }
          })
        } else {
          console.log('error submit!!');
          return false;
        }
      });
    },
    input() {
      console.log("ee")
      var regStr = /(\w)+/g;
      var regNum = /(\d)+/g;
      var reg = /_/g;
      var password = this.registerForm.password;
      var strongth = password.match(reg) && password.match(regNum) && password.match(regStr);
      if (password.length > 20 || (password.length > 6 && strongth)) {
        this.strengthClass = 'strong';
      } else if (password.length < 6) {
        this.strengthClass = 'week'
      } else if (!password) {
        this.strengthClass = 'week'
      } else {
        this.strengthClass = 'normal'
      }
    }
  }

}
</script>

<style lang="scss">
@import "@/assets/css/register/index.scss";
</style>