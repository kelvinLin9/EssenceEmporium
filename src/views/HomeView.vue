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

  <div class="container-fluid bg-primary mb-80">
    <ul class="nav container">
      <li class="nav-item">
        <a class="nav-link text-white" href="#">CHANEL</a>
      </li>
      <li class="nav-item">
        <a class="nav-link text-white" href="#">Jo Malone</a>
      </li>
      <li class="nav-item">
        <a class="nav-link text-white" href="#">Curology</a>
      </li>
      <li class="nav-item">
        <a class="nav-link text-white" href="#">Dior</a>
      </li>
      <li class="nav-item">
        <a class="nav-link text-white" href="#">Chloe </a>
      </li>
      <li class="nav-item">
        <a class="nav-link text-white" href="#">ZARA</a>
      </li> 
    </ul>
  </div>


  <div>
    <div class="container">
      <div class="row">
        <div class="col-6 col-sm-3 mb-60" v-for="item in perfumes" :key="item">
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
                <div class="subscription_Input d-flex">
                    <input class="email_input" type="text" placeholder="Your email address">
                    <a class="subscription_btn text-white w-100 d-flex justify-content-center align-items-center" href="javascript:;">Subscribe</a>
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

.subscription_Input{
	border: 2px solid #916000;
	border-radius: 4px;
	@media (min-width:540px) {
		width: 345px;
	}
	.email_input{
		padding: 18px 16px;
	}

	.subscription_btn{
		background-color: #916000;
		color: #fff;
		transition: background-color 0.3s ease ;
		&:hover{
			background-color: #6c4901;
		}
	}
}
</style>