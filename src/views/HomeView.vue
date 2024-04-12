<script setup>
import { ref } from 'vue'
import Header from '@/layout/Header.vue'
import Footer from '@/layout/Footer.vue'
import axios from 'axios';

const perfumes = ref([])
const getPerfumes = async () => {
  try {
    const res = await axios.get('https://perfume-express.onrender.com/perfumes');
    perfumes.value = res.data;
    console.log(res.data);
  } catch (error) {
    console.error(error);
  }
}

getPerfumes();
</script>

<template>
  <Header></Header>
  <div>
    <div class="container">
      <div class="row">
        <div class="col-6 col-sm-3" v-for="item in perfumes" :key="item">
          <div class="h-100 d-flex flex-column">
            <img :src="item.image" alt="香水圖片" class="perfume-img">
            <h3 class="title">
              {{ item.title }}
            </h3>
            <p class="subtitle">{{ item.category }}</p>
            <div class="">
              <span class="price">NT${{ item.originPrice }}</span>
              <span class="origin-price ms-2">NT${{ item.price }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
  <Footer></Footer>
</template>

<style scoped>
.perfume-img {
  max-width: 255px;
  aspect-ratio: 1/1;
}
.title {
  font: normal normal 600 24px/36px SF Pro Text;
}
.subtitle {
  font: normal normal 300 16px/24px SF Pro Text;
}
.price {
  font: normal normal 300 16px/24px SF Pro Text;
}
.origin-price {
  text-decoration: line-through;
  font: normal normal 300 16px/24px SF Pro Text;
  letter-spacing: 0px;
  color: #8D8D8D;
}
</style>