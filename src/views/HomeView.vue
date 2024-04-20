<script setup>
import { ref, computed } from 'vue'
import Header from '@/layout/Header.vue'
import Footer from '@/layout/Footer.vue'
import axios from 'axios';

const perfumes = ref([])
const selectedCategory = ref("")
const loading = ref(false)
const getPerfumes = async () => {
  loading.value = true
  try {
    const res = await axios.get('https://perfume-express.onrender.com/perfumes');
    perfumes.value = res.data;
    console.log(res.data);
  } catch (error) {
    console.error(error);
  } finally {
    loading.value = false
  }
}

const filterData = computed(() => {
  return perfumes.value.filter(item => item.category.match(selectedCategory.value) && item.isEnabled === true);
})

getPerfumes();
</script>

<template>
  <Header></Header>

  <div class="container-fluid bg-primary">
    <ul class="nav container">
      <li class="nav-item" @click="selectedCategory = ''">
        <a class="nav-link text-white" href="#">全部商品</a>
      </li>
      <li class="nav-item" @click="selectedCategory = '清新海洋'">
        <a class="nav-link text-white" href="#">清新海洋</a>
      </li>
      <li class="nav-item" @click="selectedCategory = '木質'">
        <a class="nav-link text-white" href="#">木質</a>
      </li>
      <li class="nav-item" @click="selectedCategory = '花香調'">
        <a class="nav-link text-white" href="#">花香調</a>
      </li>
      <li class="nav-item" @click="selectedCategory = '果香調'">
        <a class="nav-link text-white" href="#">果香調</a>
      </li>
    </ul>
  </div>

  <div v-if="loading">
    <img src="../assets/images/loading.gif" alt="">
  </div>

  <div v-if="!loading" class="mt-80">
    <div class="container">
      <div class="row">
        <div class="col-6 col-sm-3 mb-60" v-for="item in filterData" :key="item">
          <div class="h-100 d-flex flex-column">
            <img :src="item.image" alt="香水圖片" class="perfume-img">
            <h3 class="title mb-0">
              {{ item.title }}
            </h3>
            <p class="subtitle">{{ item.category }}</p>
            <div>
              <span class="price">NT${{ item.originPrice }}</span>
              <span class="origin-price ms-2">NT${{ item.price }}</span>
            </div>
            <div class="text-primary fs-20">
              <i class="bi bi-heart-fill"></i>
              <i class="bi bi-cart-fill ms-2"></i>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>

  <section class="subscription">
    <div class="container">
        <div class="row">
            <div class="col-md-4">
                <h3 class="fs-1 fw-bold c_gray mb-4">記得<br>訂閱以獲取更多資訊！</h3>
                <div class="subscription-input d-flex">
                    <input class="email-input" type="text" placeholder="Your email address">
                    <a class="subscription-btn text-white w-100 d-flex justify-content-center align-items-center" href="javascript:;">Subscribe</a>
                </div>
            </div>
        </div>
    </div>
  </section>

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

/* sub */
.subscription{
	background-image: url('../assets/images/subscribe.jpg');
	background-size: cover;
	background-repeat: no-repeat;
	background-position: center left;
	padding: 312px 0px 112px 0px;
}

.subscription-input{
	border: 2px solid #916000;
	border-radius: 4px;
	@media (min-width:540px) {
		width: 300px;
	}
	.email-input{
		padding: 12px 4px;
	}

	.subscription-btn{
		background-color: #916000;
		color: #fff;
		transition: background-color 0.3s ease ;
		&:hover{
			background-color: #6c4901;
		}
	}
}
</style>