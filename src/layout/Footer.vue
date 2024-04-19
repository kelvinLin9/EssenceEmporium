<template>
  <footer class="container-fluid bg-primary py-20">
    <div class="container">
      <div class="row">
        <div class="col-12 col-md-8 d-flex align-items-center justify-content-center justify-content-md-start">
          <div class="d-flex align-items-center text-white">
            <h1>
              <RouterLink to="/" class="logo navbar-brand nav-link d-flex">
                <span>香水電商</span>
              </RouterLink>
            </h1>
            <p class="ms-md-4 ps-20">© 2020. All Rights Reserved.</p>

          </div>
        </div>
        <div class="col-12 col-md-4">
          <ul class="d-flex align-items-center justify-content-center justify-content-md-end text-white pt-3">
            <li class="fs-6 me-2">
              <a href="#" class="text-white">Product</a></li>
            <li class="fs-6 me-2">
              <a href="#" class="text-white">Blog</a></li>
            <li class="fs-6">
              <a href="#" class="text-white">Contact</a></li>
          </ul>
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