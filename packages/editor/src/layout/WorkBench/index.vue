<template>
  <div class="workbench__wrap">
    <div class="menu__wrap">
      <el-menu class="el-menu-vertical-demo" :collapse="true">
        <div @click="handleClick('asset')">
          <el-menu-item>
            <el-icon>
              <Star />
            </el-icon>
            <template #title>物料区</template>
          </el-menu-item>
        </div>

        <div @click="handleClick('outlines')">
          <el-menu-item>
            <el-icon>
              <Document />
            </el-icon>
            <template #title>大纲树</template>
          </el-menu-item>
        </div>

        <div @click="handleClick('code')">
          <el-menu-item>
            <el-icon>
              <Aim />
            </el-icon>
            <template #title>代码编辑区</template>
          </el-menu-item>
        </div>
      </el-menu>
    </div>
    <div class="list__wrap" v-if="currentShow === 'asset'">
      <ElementList />
    </div>
    <div class="tree__wrap" v-if="currentShow === 'outlines'">
      <OutlinesTree />
    </div>
    <div class="code__wrap" v-show="currentShow === 'code'">
      <Code />
    </div>
  </div>
</template>

<script lang="ts" setup>
import ElementList from "./components/elementList/index.vue";
import { Document, Star, Aim } from "@element-plus/icons-vue";
import { ref } from "vue";
import OutlinesTree from "./components/OutlinesTree/index.vue";
import Code from "./components/Code/index.vue";

const currentShow = ref<string>("asset");

const handleClick = (tabName: string) => {
  if (currentShow.value === tabName) {
    currentShow.value = "";
  } else {
    currentShow.value = tabName;
  }
  return true;
};
</script>

<style lang="scss" scoped>
.workbench__wrap {
  width: 100%;
  height: 100%;
  display: flex;
  .menu__wrap {
    width: 64px;
    height: 100%;
  }

  .list__wrap {
    padding: 10px;
    width: 300px;
  }
  .tree__wrap {
    padding: 10px;
    width: 200px;
  }
  .code__wrap {
    padding: 10px;
    width: 400px;
  }
}
::v-deep(.el-menu--collapse) {
  height: 100%;
}
::v-deep(.el-menu-item.is-active) {
  color: black;
}
</style>
