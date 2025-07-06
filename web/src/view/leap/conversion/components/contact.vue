<template>
  <div class="app-container">
    <el-table :data="tableData" style="width: 100%">
      <el-table-column prop="name" label="姓名"></el-table-column>
      <el-table-column prop="email" label="邮箱"></el-table-column>
      <el-table-column prop="address" label="地址"></el-table-column>
    </el-table>
    <el-pagination
      @size-change="handleSizeChange"
      @current-change="handleCurrentChange"
      :current-page="currentPage"
      :page-sizes="[100, 200, 300, 400]"
      :page-size="100"
      layout="total, sizes,prev, pager, next, jumper"
      :total="400"
      style="margin-top: 20px"
    ></el-pagination>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
const tableData = ref([]);
const currentPage = ref(1);
const handleSizeChange = (val: any) => {
  console.log(`每页 ${val} 条`);
};
const handleCurrentChange = (val: any) => {
  console.log(`当前页: ${val}`);
};
</script>

<style lang="scss" scoped></style>
