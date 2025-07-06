<template>
  <div class="app-container">
    <el-card>
      <p>开始与你的潜在投资人进行互动</p>
      <el-tabs v-model="activeName">
        <el-tab-pane label="付款" name="first">
          <Pay></Pay>
        </el-tab-pane>
        <el-tab-pane label="电子邮箱" name="second">
          <Email></Email>
        </el-tab-pane>
        <el-tab-pane label="联系人" name="third">
          <Contact></Contact>
        </el-tab-pane>
      </el-tabs>
    </el-card>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
import Pay from "./components/pay.vue";
import Email from "./components/email.vue";
import Contact from "./components/contact.vue";

const activeName = ref("first");
</script>

<style lang="scss" scoped></style>
