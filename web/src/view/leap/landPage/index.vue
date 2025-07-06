<template>
  <div class="landPage">
    <el-header>
      <div class="leftArea">
        <div class="name">Strenger</div>
        <div class="description">Changes will be saved automatically</div>
      </div>
      <div class="rightArea">
        <div class="color">
          <svg-icon
            name="icon-palette"
            style="width: 40px; height: 40px; color: red"
          />
        </div>
        <div class="share">Share</div>
        <div class="publish">Publish</div>
      </div>
    </el-header>
    <el-main>
      <div class="content">
        <GridLayout
          :layout.sync="layout"
          :col-num="12"
          :row-height="30"
          :is-draggable="true"
          :is-resizable="true"
          @layout-updated="logLayout"
        >
          <GridItem
            v-for="item in layout"
            :key="item.i"
            :x="item.x"
            :y="item.y"
            :w="item.w"
            :h="item.h"
            :i="item.i"
          >
            <Text :id="item.i" v-if="item.type === 'text'" />
            <Image :id="item.i" v-if="item.type === 'image'" />
          </GridItem>
        </GridLayout>
      </div>
    </el-main>
    <el-footer></el-footer>
  </div>
</template>

<script setup lang="ts">
  import { ref } from 'vue'
  import { GridLayout, GridItem } from 'vue3-grid-layout'
  import Text from './components/text.vue'
  import Image from './components/image.vue'

  // 前端模拟数据
  const layout = ref([
    { x: 0, y: 0, w: 2, h: 2, i: '1', type: 'text' },
    { x: 2, y: 0, w: 2, h: 4, i: '2', type: 'image'}
  ])

  // 添加卡片
  const addItem = () => {
    const newId = Date.now().toString()
    layout.value.push({
      x: 0,
      y: Infinity, // 自动放到最底部
      w: 2,
      h: 2,
      i: newId,
      type: 'text'
    })
  }

  // 删除卡片
  const removeItem = (id: string) => {
    layout.value = layout.value.filter((item) => item.i !== id)
  }

  // 重置布局
  const resetLayout = () => {
    layout.value = [
      { x: 0, y: 0, w: 2, h: 2, i: '1', type: 'text' },
      { x: 2, y: 0, w: 2, h: 4, i: '2', type: 'image' }
    ]
  }

  // 打印当前布局（开发调试用）
  const logLayout = () => {
    console.log('当前布局:', JSON.parse(JSON.stringify(layout.value)))
  }
</script>

<style scoped>
  .landPage {
    width: 100%;
    height: 50px;
    .el-header {
      width: 100%;
      height: 100%;
      display: flex;
      align-items: center;
      justify-content: space-between;
      .leftArea {
        display: flex;
        align-items: center;
        .name {
          font-size: 16px;
          font-weight: bold;
        }
        .description {
          font-size: 12px;
          margin-left: 10px;
        }
      }
      .rightArea {
        display: flex;
        align-items: center;
        > div {
          height: 34px;
          cursor: pointer;
          border-radius: 5px;
          line-height: 34px;
          text-align: center;
          font-size: 14px;
          font-weight: 400;
        }
        .color {
          margin-right: 10px;
          width: 50px;
          display: flex;
          align-items: center;
          justify-content: center;
          border: 1px solid rgb(209 213 219);
        }
        .share {
          margin-right: 10px;
          width: 72px;
          border: 1px solid rgb(209 213 219);
          color: black;
          background-color: white;
        }
        .publish {
          width: 72px;
          background-color: rgb(16 185 129);
          color: white;
        }
      }
    }
  }

  .el-main {
    width: 100%;
    height: 80vh;
    background-color: hotpink;
    .content {
      width: 100%;
      height: 100%;
      .vue-grid-layout {
        min-height: 100%;
        width: 100%;
        .grid-item {
          border: 1px solid #ddd;
        }
      }
    }
  }

  .el-footer {
    width: 100%;
    height: 100%;
  }
</style>
