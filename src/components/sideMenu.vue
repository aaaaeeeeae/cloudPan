<template>
    <div class="side-Menu">
        <el-menu default-active="1-1" class="el-menu-vertical-demo">
            <div class="side-Menu-content">
                <el-sub-menu index="1" class="item">
                    <template #title>
                        <el-icon>
                            <MessageBox />
                        </el-icon>
                        <span>我的文件</span>
                    </template>
                    <el-menu-item index="1-1">
                        <el-icon>
                            <Menu />
                        </el-icon>
                        <span>全部</span>
                    </el-menu-item>
                    <el-menu-item index="1-2">
                        <el-icon>
                            <Picture />
                        </el-icon>
                        <span>图片</span>
                    </el-menu-item>
                    <el-menu-item index="1-3">
                        <el-icon>
                            <Document />
                        </el-icon>
                        <span>文档</span>
                    </el-menu-item>
                    <el-menu-item index="1-4">
                        <el-icon>
                            <VideoCameraFilled />
                        </el-icon>
                        <span>视频</span>
                    </el-menu-item>
                    <el-menu-item index="1-5">
                        <el-icon>
                            <Headset />
                        </el-icon>
                        <span>音乐</span>
                    </el-menu-item>
                    <el-menu-item index="1-6">
                        <el-icon>
                            <Files />
                        </el-icon>
                        <span>其他</span>
                    </el-menu-item>
                </el-sub-menu>
                <el-menu-item index="2" class="item">
                    <el-icon>
                        <Delete />
                    </el-icon>
                    <span>回收站</span>
                </el-menu-item>
                <el-menu-item index="3" class="item">
                    <el-icon>
                        <Share />
                    </el-icon>
                    <span>我的分享</span>
                </el-menu-item>
                <div class="progress-bar">
                    <el-progress :percentage="percentage" :show-text="false" type="line" stroke-width="4"
                        stroke-linecap="square" class="progress"></el-progress>
                    <span>内存条20%</span>
                </div>
            </div>

        </el-menu>

    </div>
</template>

<script setup lang="ts">
import { ref } from "vue"
import {
    Delete,
    MessageBox,
    Share,
    Menu,
    Picture,
    Document,
    VideoCameraFilled,
    Headset,
    Files
} from '@element-plus/icons-vue'
const percentage = ref(20)
</script>

<style scoped>
.side-Menu {
    width: 20vw;
    height: 90vh;

    .side-Menu-content {
        height: 90vh;
        .item{
            box-shadow: 0 3px 10px #f7f9fc;
        }
        .progress-bar {
            display: flex;
            flex-direction: column;
            justify-content: center;
            align-items: center;
            height: 60px;
            width: 100%;
            position: absolute;
            bottom: 0px;
            box-shadow: 0 -3px 10px #f7f9fc;
            .progress{
                width: 80%;
                margin-bottom: 10px;
            }
        }
    }
}
</style>
