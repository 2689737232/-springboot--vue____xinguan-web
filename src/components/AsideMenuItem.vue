<template>
  <div id="aside-menu-item-wrapper">
    <!-- 【如果有子项的布局样式】 -->
    <template v-if="item.children.length>0">
      <!-- 绑定每一项的id和parentId -->
      <el-submenu :index="item.id" :parentId="item.paparentId">
        <!-- 父标签 名和样式 -->
        <template slot="title">
          <i :class="item.icon"></i>
          <!-- 父列表名 -->
          <span>{{item.menuName}}</span>
        </template>
        <!-- 循环每一个子项 递归创建每一个子项 -->
        <template v-for="_item in item.children">
          <el-menu-item-group :key="_item.id">
            <!-- 递归创建 -->
            <aside-menu-item :item="_item"></aside-menu-item>
          </el-menu-item-group>
        </template>
      </el-submenu>
    </template>
    <!-- 【如果没有子项的布局样式】 递归出口 -->
    <template v-else>
      <el-menu-item
        :class="item.icon"
        :index="item.id"
        :parentId="item.paparentId"
      >{{item.menuName}}</el-menu-item>
    </template>
  </div>
</template>
<script>
/**
 * @description: 用于创建侧边栏每一项菜单的组件
 * @author: lala
 * @date: 2020-10-18 17:32:35
 */
export default {
  // 组件名字
  name: "AsideMenuItem",
  props: {
    item: {
      type: Object,
      require: false,
    },
  },
  methods: {},
  created() {
    //  console.log(this);
  },
};
</script>

<style scoped>
</style>


