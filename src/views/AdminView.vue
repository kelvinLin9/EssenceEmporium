<template>
<div>
  <div class="container mt-5">
    <h1 class="mb-4">香水電商後台管理</h1>
    <button 
      class="btn btn-primary mb-3"
      data-bs-toggle="modal" 
      data-bs-target="#createPerfumeModal"
    >
      新增產品
    </button>
    <table class="table table-striped">
      <thead>
        <tr>
          <th scope="col">#</th>
          <th scope="col">圖片</th>
          <th scope="col">名稱</th>
          <th scope="col">類別</th>
          <th scope="col">價格</th>
          <th scope="col">容量</th>
          <th scope="col">操作</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(product, index) in perfumesData" :key="product._id">
          <th scope="row">{{ index + 1 }}</th>
          <td><img :src="product.image" alt="product image" class="img-thumbnail" style="width: 100px;"></td>
          <td>{{ product.title }}</td>
          <td>{{ product.category }}</td>
          <td>${{ product.price }}</td>
          <td>{{ product.unit }}</td>
          <td>
            <button 
              class="btn btn-primary btn-sm me-8" 
              data-bs-toggle="modal" 
              data-bs-target="#editMyCourseModal" 
              @click="editProduct(product)">
                編輯
            </button>
            <button class="btn btn-danger btn-sm" @click="deletePerfumes(product._id)">刪除</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
  <EditPerfumeModal :product="currentProduct" @update="getPerfumes"/>
  <CreatePerfumeModal @update="getPerfumes"/>

</div>




</template>

<script setup>
import EditPerfumeModal from '@/components/EditPerfumeModal.vue'
import CreatePerfumeModal from '@/components/CreatePerfumeModal.vue'
import axios from 'axios';
import { ref } from 'vue';

const perfumesData = ref([])
const currentProduct = ref(null);

function editProduct(product) {
  currentProduct.value = product;
}

const getPerfumes = async () => {
  try {
    const res = await axios.get('https://perfume-express.onrender.com/perfumes');
    perfumesData.value = res.data;
    console.log(perfumesData.value)
  } catch (error) {
    console.log(error);
  }
}
getPerfumes();

const deletePerfumes = async (id) => {
  console.log(id)
  try {
    const res = await axios.delete(`https://perfume-express.onrender.com/perfumes/${id}`);
    console.log(res.data);
    getPerfumes();
  } catch (error) {
    console.log(error);
  }

}
</script>


<style scoped>
.img-thumbnail {
  width: 100px;
  height: 100px;
  object-fit: cover; /* 保持图片比例，多余部分将被裁剪 */
}
</style>


