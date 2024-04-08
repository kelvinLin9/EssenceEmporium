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
        <div class="col-3" v-for="item in perfumes">
          <div class="h-100 d-flex flex-column">
            <img :src="item.image" alt="香水圖片" class="perfume-img">
            <h3 class="">
              {{ item.title }}
            </h3>
            <p>{{ item.category }}</p>
            <div class="">
              <span>{{ item.originPrice }}</span>
              <span>{{ item.price }}</span>
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
  height: 255px;
}
</style>