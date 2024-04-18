<template>
  <div class="container">
    <nav class="navbar navbar-expand-lg">
      <div class="container-fluid">
        <h1>
          <RouterLink to="/" class="logo navbar-brand nav-link d-flex">
            <span>香水電商</span>
          </RouterLink>
        </h1>


        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarSupportedContent">
          <ul class="navbar-nav ms-auto mb-2 mb-lg-0 d-flex align-items-center menu">
            <li class="nav-item d-flex align-items-center">
              <i class="bi bi-shop"></i>
              <a class="nav-link" aria-current="page" href="#">Product</a>
            </li>
            <li class="nav-item d-flex align-items-center ms-7">
              <i class="bi bi-person-fill"></i>
              <a class="nav-link" aria-current="page" href="#">Log In</a>
            </li>
            <li class="nav-item d-flex align-items-center">
              <i class="bi bi-cart-fill"></i>
              <a class="nav-link" href="#">Cart(3)</a>
            </li>
            <RouterLink class="nav-item d-flex align-items-center" to="/admin">
              <i class="bi bi-tools"></i>
              <a class="nav-link">Admin</a>
            </RouterLink>
          </ul>
        </div>
      </div>
    </nav>
  </div>
</template>

<script setup>
</script>

<style lang="scss" scoped>
.logo {
    background-image: url(../assets/images/d’Perfume.png);
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
.bi {
  margin-left: 28px;
}
.menu {
  color: #8D8D8D;
}
</style>
