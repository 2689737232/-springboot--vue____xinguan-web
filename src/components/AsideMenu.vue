
<template>
  <div id="aside-menu-wrapper">
    <el-button class="btn-nfold" type="primary" @click="handleUnfold">|||</el-button>
    <el-row>
      <!-- 侧边栏 -->
      <el-col class="aside-bar" :span="12">
        <el-menu
          :collapse-transition="false"
          default-active="2"
          class="el-menu-vertical-demo"
          @open="handleOpen"
          @close="handleClose"
          :collapse="isCollapse"
          background-color="#545c64"
          text-color="#fff"
          active-text-color="#ffd04b"
        >
          <!-- 根据传入的菜单列表循环创建  -->
          <template v-for="item in menuList">
            <aside-menu-item :item="item" :key="item.id"></aside-menu-item>
          </template>
        </el-menu>
      </el-col>
    </el-row>
  </div>
</template>

<script>
/**
 * @description: 侧边栏组件
 * @author: lala
 * @date: 2020-10-18 17:32:20
 */
import AsideMenuItem from "../components/AsideMenuItem";

export default {
  props: {
    menuList: {
      type: Array,
      required: false,
    },
  },
  data() {
    return {
      //用于保存是否显示侧边导航的变量
      isCollapse: true,
    };
  },
  methods: {
    handleOpen(key, keyPath) {
      console.log(key, keyPath);
    },
    handleClose(key, keyPath) {
      console.log(key, keyPath);
    },
    //  展开隐藏侧边栏
    handleUnfold() {
      this.isCollapse = !this.isCollapse;
    },
  },
  components: {
    AsideMenuItem,
  }
};
</script>

<style lang="less" scoped>
@full-height: 100%;
@full-width: 100%;
.full-width-height {
  height: @full-height;
  width: @full-width;
}
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
</style>