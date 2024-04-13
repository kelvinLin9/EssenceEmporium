<template>
  <footer class="container-fluid bg-primary py-20">
    <div class="container">
      <div class="row justify-content-between">
        <div class="col">
          <div class="d-flex align-items-center text-white">
            <h1>
              <RouterLink to="/" class="logo navbar-brand nav-link d-flex">
                <span>香水電商</span>
              </RouterLink>
            </h1>
            <p class="ms-md-4 ps-20">© 2020. All Rights Reserved.</p>
            <div class="ms-auto">
              <ul class="mb-2 mb-lg-0 d-flex align-items-center menu text-white">
                <li class="c_ml_36 fs-5">
                  <a href="#" class="text-white">Product</a></li>
                <li class="c_ml_36 fs-5">
                  <a href="#" class="text-white">Blog</a></li>
                <li class="c_ml_36 fs-5">
                  <a href="#" class="text-white">Contact</a></li>
              </ul>
            </div>
          </div>
        </div>
      </div>
    </div>
  </footer>
</template>

<script setup>
</script>

<style scoped>
.logo {
    background-image: url(../assets/images/d’Perfumew_w.png);
    background-size: cover;
    background-position: center center;
    width: 128px;
    height: 38px;
    display: block;
    overflow: hidden;
    white-space: nowrap;
    text-indent: -9999px;
    color: transparent; 
}
</style>