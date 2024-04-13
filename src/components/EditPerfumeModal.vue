<template>
  <div class="modal fade" id="editMyCourseModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true" data-bs-backdrop="static">
    <div class="modal-dialog">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title" id="editPerfumeModalLabel">编辑香水</h5>
          <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
        </div>
        <div class="modal-body">
          <form @submit.prevent="submitForm">
            <div class="mb-3">
              <label for="title" class="form-label">名稱</label>
              <input type="text" class="form-control" id="title" v-model="perfumeData.title" required>
            </div>
            <div class="mb-3">
              <label for="category" class="form-label">類別</label>
              <input type="text" class="form-control" id="category" v-model="perfumeData.category" required>
            </div>
            <div class="mb-3">
              <label for="price" class="form-label">價格</label>
              <input type="number" class="form-control" id="price" v-model.number="perfumeData.price" required>
            </div>
            <div class="mb-3">
              <label for="unit" class="form-label">容量</label>
              <input type="text" class="form-control" id="unit" v-model="perfumeData.unit" required>
            </div>
            <div class="mb-3">
              <label for="image" class="form-label">圖片連結</label>
              <input type="url" class="form-control" id="image" v-model="perfumeData.image" required>
            </div>
            <button 
              type="submit" 
              class="btn btn-primary" 
              aria-label="Close" 
              data-bs-dismiss="modal"
              @click="editPerfumes">
                保存
              </button>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, watch, defineProps, defineEmits } from 'vue';
import  axios  from 'axios';

const props = defineProps({
  product: Object
});

const emits = defineEmits(['update']);

const perfumeData = ref({});

watch(() => props.product, (newVal) => {
  perfumeData.value = {...newVal};
}, { deep: true, immediate: true });

const editPerfumes = async() => {
  console.log(perfumeData.value)
  try {
    const res = await axios.patch(`https://perfume-express.onrender.com/perfumes/${perfumeData.value._id}`, perfumeData.value);
    perfumeData.value = res.data;
    console.log(perfumeData.value);
    emits('update')
  } catch (error) {
    console.error(error);
  }
};

</script>

<style scoped>

</style>
