
<template>
  <div class="grid-demo">
    <button @click="addItem">添加卡片</button>
    <button @click="resetLayout">重置布局</button>

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
        <Text :id="item.i" v-if="item.type === 'text'"/>
        <Image :id="item.i" v-if="item.type === 'image'"/>
      </GridItem>
    </GridLayout>
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
  .grid-demo {
    padding: 20px;
    height: 80vh; /* 或固定像素高度 */
    position: relative;
  }
  .grid-card {
    height: 100%;
    padding: 12px;
    background: #fff;
    border: 1px solid #ebeef5;
    border-radius: 4px;
  }
  .vue-grid-layout {
    background: #f5f7f9;
    min-height: 100%;
    width: 100%;
  }
  .gva-container2 {
    height: calc(100vh - 120px) !important; /* 确保容器有固定高度 */
    position: relative;
  }
  .grid-item {
    border: 1px solid #ddd;
    background: #fff;
  }
</style>
