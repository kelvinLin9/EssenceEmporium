<template>
  <div>
    <!-- 導航列 -->
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
      <div class="container-fluid">
        <a class="navbar-brand" href="#">香水管理後台</a>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNav">
          <ul class="navbar-nav">
            <li class="nav-item">
              <a class="nav-link active" aria-current="page" href="#">首頁</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#">香水列表</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#">新增香水</a>
            </li>
          </ul>
        </div>
      </div>
    </nav>

    <!-- 頁面內容 -->
    <div class="container mt-5">
      <h2>香水列表</h2>
      <!-- 表格 -->
      <table class="table">
        <thead>
          <tr>
            <th scope="col">#</th>
            <th scope="col">標題</th>
            <th scope="col">類別</th>
            <th scope="col">價格</th>
            <th scope="col">操作</th>
          </tr>
        </thead>
        <tbody>
          <!-- 表格內容將在這裡填充 -->
        </tbody>
      </table>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import axios from 'axios';

const getPerfumes = async () => {
  try {
    const response = await axios.get('https://perfume-express.onrender.com/perfumes');
    console.log(response.data);
  } catch (error) {
    console.error(error);
  }
}

getPerfumes();
</script>

<style>
/* 你可以在這裡添加額外的CSS樣式 */
</style>
