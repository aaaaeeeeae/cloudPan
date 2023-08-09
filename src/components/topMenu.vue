<template>
    <div class="top-Menu-content">
        <el-menu :default-active="activeIndex" class="el-menu-demo" mode="horizontal" :ellipsis="false">
            <div>logo</div>
            <el-menu-item index="1">首页</el-menu-item>
            <el-menu-item index="2">网盘</el-menu-item>
            <div class="flex-grow" />
            <div class="el-menu-item nobgColor">登录</div>
            <div class="el-menu-item nobgColor">退出</div>

        </el-menu>
    </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const activeIndex = ref('1')

</script>

<style scoped>
.top-Menu-content {
    width: 100%;

    .el-menu-demo {
        height: 10vh;

    }

    .flex-grow {
        flex-grow: 1;
    }

    .nobgColor {
        background-color: transparent !important;
        padding-right: 50px;
    }

}
</style>
