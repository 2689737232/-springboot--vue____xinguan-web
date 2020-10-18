<template>
  <div id="login-wrapper">
    <el-container>
      <el-main>
        <div class="login-box">
          <!-- 头部用户图标 -->
          <el-button class="user-icon" circle></el-button>

          <el-row>
            <el-col :span="18" :offset="3">
              <div class="grid-content bg-purple-dark">
                <el-input prefix-icon="el-icon-s-custom" v-model="userName" placeholder="用户名/账号"></el-input>
              </div>
            </el-col>
          </el-row>
          <el-row>
            <el-col :span="18" :offset="3">
              <div class="grid-content bg-purple-dark">
                <el-input
                  prefix-icon="el-icon-lock"
                  show-password
                  v-model="userPassword"
                  placeholder="密码"
                ></el-input>
              </div>
            </el-col>
          </el-row>
          <el-row>
            <el-col :span="10" :offset="3">
              <div class="grid-content bg-purple-dark">
                <el-input prefix-icon="el-icon-lock" v-model="authCode" placeholder="验证码"></el-input>
              </div>
            </el-col>
            <!-- 验证码区域 -->
            <el-col :span="5" :offset="3">
              <img @click="getOtherCodeImg" class="auth-code" :src="authCodeUrl" alt="验证码" />
            </el-col>
          </el-row>
          <!-- 按钮区域 -->
          <el-row class="btn-box">
            <el-col :span="18" :offset="8">
              <el-button @click="loginIn" type="primary">登录</el-button>
              <el-button @click="reset">重置</el-button>
            </el-col>
          </el-row>
        </div>
      </el-main>
    </el-container>
  </div>
</template>

<script>
import "@/common-style/init.css";
export default {
  data() {
    return {
      fit: "验证码",
      userName: "",
      userPassword: "",
      authCode: "",
      authCodeUrl: "https://s2.ax1x.com/2019/08/23/msFrE8.png",
    };
  },
  methods: {
    //   获取下一张验证码
    getOtherCodeImg() {
      console.log("获取另外一张验证码图片");
    },
    //  登录
    loginIn() {
      console.log("登录");
    },
    //  重置
    reset() {
      this.userName = "";
      this.userPassword = "";
      this.authCode = "";
    },
  },
};
</script>

<style lang="less" scoped>
.full-width-height {
  width: 100%;
  height: 100%;
}

#login-wrapper {
  overflow: hidden;
  height: 100vh;
  width: 100vw;

  .el-container {
    .full-width-height;

    .el-main {
      .full-width-height;
      padding: 0;
      background-color: #40a0ffa2;
      color: #333;
      text-align: center;
      box-sizing: border-box;
      display: flex;
      justify-content: center;
      align-items: center;
    }

    // 中间的登录盒子
    .login-box {
      //  用户头像的边长
      @user-icon-length: 150px;

      position: relative;
      padding: @user-icon-length / 2 15px 15px 15px;
      background-color: white;
      width: 30%;
      &:hover {
        box-shadow: 0 0 15px 3px rgb(156, 156, 156);
      }
      // 用户头像
      .user-icon {
        position: absolute;
        cursor: pointer;
        left: 50%;
        width: @user-icon-length;
        height: @user-icon-length;
        transform: translateX(-50%) translateY(-100%);
        font-size: @user-icon-length / 3;
        background: url("../assets/img/User Icon.jpg");
        background-size: cover;
        background-position: center center;
        background-repeat: no-repeat;
        transition: width,height 0.2s cubic-bezier(0, 1.82, 0.69,-0.4);
        &:hover {
          box-shadow: 0 0 5px 2px rgb(160, 160, 160);
          width: @user-icon-length + 15%;
          height: @user-icon-length + 15%;
          background-image: url("../assets/img/User Hover.jpg");
        }
      }
      // 验证码
      .auth-code {
        .full-width-height;
      }
      // 登录重置
      .btn-box {
        margin-top: 35px;
      }
    }
  }
}

// el-row 通用设置
.el-row {
  margin-top: 25px;
}
</style>