<template>
  <div id="home-wrapper">
    <el-container>
      <!-- 顶部导航 -->
      <el-header class="top-nav">
        <el-row :gutter="20">
          <el-col class="icon-el-col" :span="4">
            <el-image class="nav-img" :src="logo"></el-image>
            <span class="title">物资管理系统</span>
          </el-col>
          <el-col class="user-el-col" :span="1" :offset="17">
            <!-- 用户头像区域 -->
            <el-image class="nav-img" :src="userIcon"></el-image>
          </el-col>
        </el-row>
      </el-header>
      <!-- 导航、主体 -->
      <el-container class="content-box">
        <el-aside>
          <!-- 菜单栏组件 -->
          <aside-menu :menuList="menuList"></aside-menu>
        </el-aside>
        <!-- 主内容区域 -->
        <el-main>Main</el-main>
      </el-container>
    </el-container>
  </div>
</template>

<script>
import "../common-style/init.css";
import AsideMenu from "../components/AsideMenu";
import axios from "axios";

export default {
  components: {
    AsideMenu,
  },
  data() {
    return {
      userIcon: require("../assets/img/user.png"),
      logo: require("../assets/img/logo.png"),
      // 是否展开侧边栏
      isCollapse: false,
      // 左侧菜单栏的数据
      menuList: null,
    };
  },
  methods: {},
  created() {
    //  模拟数据获取
    axios
      .get("http://mockjs.wuzi.menu.list")
      .then((res) => {
        if (res) {
          this.menuList = res.data.MenuList;
        }
      })
      .catch((err) => {
        console.log(err);
      });
  },
};
</script>



<style lang="less" scoped>

/**
  变量定义
*/
@full-width: 100%;
@full-height: 100%;

.full-width-height {
  height: @full-height;
  width: @full-width;
}


/**
  样式设置
*/
#home-wrapper {
  width: 100vw;
  height: 100vh;
  .el-container {
    .full-width-height;
    // 顶部导航栏
    .top-nav {
      .full-width-height;
      background-color: rgb(0, 36, 88);
      .el-col {
        height: @full-height;
        .nav-img {
          height: 45px;
          width: 45px;
          margin-top: 6px;
          background-color: white;
          border-radius: 50%;
          background-size: 80% 80%;
          background-position: center center;
        }

        &.user-el-col {
          transform: translateX(110%);
        }

        .title {
          padding-left: 15px;
          display: inline-block;
          height: 100%;
          font-size: 16px;
          font-weight: bold;
          color: white;
          line-height: 60px;
          vertical-align: top;
        }
      }
    }

    .content-box {
      position: relative;
      overflow-x: hidden;
      // 侧边栏
      .el-aside {
        position: absolute;
        width: auto !important;
        padding-right: 5px;
        height: max-content;

        .el-menu {
          width: @full-width;
          height: @full-height;
          display: inline-block;
        }
        .aside-bar {
          width: @full-width;
        }
        .btn-nfold {
          width: 100%;
        }
      }
      // 展示区
      .el-main {
        box-sizing: border-box;
        padding-left: 300px;
        height: 100vh;
      }
    }
  }
}

// element初始化
.el-header,
.el-footer {
  padding: 0;
  margin: 0;
  color: #333;
  text-align: center;
  line-height: 60px;
}

.el-aside {
  background-color: #d3dce6;
  color: #333;
  text-align: center;
}

.el-main {
  background-color: #e9eef3;
  color: #333;
  text-align: center;
  line-height: 160px;
}

.el-row {
  width: @full-width;
  margin-bottom: 20px;
  margin-left: 0 !important;
  margin-right: 0 !important;
  .full-width-height;
  &:last-child {
    margin-bottom: 0;
  }
}
.el-col {
  border-radius: 4px;
}
</style>