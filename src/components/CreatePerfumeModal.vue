
當然，這裡提供了完整的CreatePerfumeModal.vue組件，所有文本和屬性均使用繁體中文，以符合您的需求。

CreatePerfumeModal.vue 更新
這個版本的CreatePerfumeModal組件包括了所有必要的欄位：category (分類), image (圖片連結), isEnabled (是否啟用), originPrice (原價), price (售價), title (名稱), 和 unit (單位)。

vue
Copy code
<template>
  <div class="modal fade" id="createPerfumeModal" tabindex="-1" aria-labelledby="createPerfumeModalLabel" aria-hidden="true" data-bs-backdrop="static">
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="createPerfumeModalLabel">新增香水</h5>
          <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
        </div>
        <div class="modal-body">
          <form @submit.prevent="createPerfume">
            <div class="mb-3">
              <label for="title" class="form-label">名稱</label>
              <input type="text" class="form-control" id="title" v-model="perfumeData.title" required>
            </div>
            <div class="mb-3">
              <label for="category" class="form-label">類別</label>
              <input type="text" class="form-control" id="category" v-model="perfumeData.category" required>
            </div>
            <div class="mb-3">
              <label for="price" class="form-label">售價</label>
              <input type="number" class="form-control" id="price" v-model.number="perfumeData.price" required>
            </div>
            <div class="mb-3">
              <label for="originPrice" class="form-label">原價</label>
              <input type="number" class="form-control" id="originPrice" v-model.number="perfumeData.originPrice" required>
            </div>
            <div class="mb-3">
              <label for="unit" class="form-label">庫存單位</label>
              <input type="text" class="form-control" id="unit" v-model="perfumeData.unit" required>
            </div>
            <div class="mb-3">
              <label for="image" class="form-label">圖片連結</label>
              <input type="url" class="form-control" id="image" v-model="perfumeData.image" required>
            </div>
            <div class="mb-3 form-check">
              <input type="checkbox" class="form-check-input" id="isEnabled" v-model="perfumeData.isEnabled">
              <label for="isEnabled" class="form-check-label">啟用</label>
            </div>
            <button 
              type="submit" 
              class="btn btn-primary"
              aria-label="Close" 
              data-bs-dismiss="modal"
            >
              保存
            </button>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, defineEmits } from 'vue';
import axios from 'axios';

const perfumeData = ref({
  title: '',
  category: '',
  price: 0,
  unit: '',
  image: '',
  isEnabled: false,
});
const emits = defineEmits(['update']);
const createPerfume = async () => {
  try {
    const res = await axios.post('https://perfume-express.onrender.com/perfumes', perfumeData.value);
    console.log(res.data);
    perfumeData.value = { title: '', category: '', price: 0, unit: '', image: '', isEnabled: false};
    emits('update')
  } catch (err) {
    console.log('Failed to create perfume:', err);
  }
};
</script>

<style scoped>
/* Optional custom styles */
</style>
