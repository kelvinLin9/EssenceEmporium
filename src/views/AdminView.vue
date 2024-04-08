<template>
  <div>
    <button type="button" class="btn btn-outline-primary w-25"
      data-bs-toggle="modal" data-bs-target="#editMyCourseModal">
      編輯
    </button>
  </div>
  <EditPerfumeModal/>

</template>

<script setup>
import EditPerfumeModal from '@/components/EditPerfumeModal.vue'
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
