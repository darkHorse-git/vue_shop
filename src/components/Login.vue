<template>
  <div class="login_container">
    <div class="login_box">
      <!--头像区域-->
      <div class="avatar_box">
        <img src="../assets/logo.png" />
      </div>
      <!-- 登录框 -->
      <el-form ref="loginFormRef" class="login_form" :model="loginForm" :rules="loginFormRule">
        <!-- 用户名输入 -->
        <el-form-item prop="username">
          <el-input
            v-model="loginForm.username"
            prefix-icon="iconfont icon-user"
            placeholder="请输入登录名"
            autofocus
          ></el-input>
        </el-form-item>
        <!--密码输入框 -->
        <el-form-item prop="password">
          <el-input
            prefix-icon="iconfont icon-3702mima"
            placeholder="请输入登录密码"
            v-model="loginForm.password"
            show-password
          ></el-input>
        </el-form-item>
        <!-- 按钮 -->
        <el-form-item class="btns">
          <el-button type="primary">登录</el-button>
          <el-button type="info" @click="resetLoginForm">重置</el-button>
        </el-form-item>
      </el-form>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      loginForm: {
        username: "",
        password: ""
      },
      loginFormRule: {
        username: [
          { required: true, message: "请输入登录名", trigger: "blur" },
          { min: 3, max: 10, message: "长度在 3 到 10 个字符", trigger: "blur" }
        ],
        password: [
          { required: true, message: "请输入登录密码", trigger: "blur" },
          { min: 6, max: 15, message: "长度在 3 到 15 个字符", trigger: "blur" }
        ]
      }
    };
  },
  methods: {
    // 点击重置按钮
    resetLoginForm() {
      this.$refs.loginFormRef.resetFields();
    }
  }
};
</script>
<style lang='less' scoped>
.login_container {
  background-color: #0d759e;
  height: 100%;
}

.login_box {
  width: 480px;
  height: 320px;
  border-radius: 5px;
  background-color: #fff;
  position: absolute;
  margin: auto;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;

  .avatar_box {
    width: 130px;
    height: 130px;
    border: 1px solid #fff;
    background-color: #0d759e;
    border-radius: 50%;
    padding: 10px;
    position: absolute;
    left: 50%;
    transform: translate(-50%, -50%);

    img {
      width: 100%;
      height: 100%;
      border-radius: 50%;
      background-color: #028d48;
    }
  }
}

.login_form {
  position: absolute;
  left: 0;
  bottom: 0;
  width: 100%;
  padding: 0 15px;
  box-sizing: border-box;

  .btns:last-child {
    display: flex;
    justify-content: flex-end;
  }
}
</style>