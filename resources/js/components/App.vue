<template>

  <div class="container">
    <header>
      <div class="px-3 py-2 bg-dark text-white">
        <div class="container">
          <div class="d-flex flex-wrap align-items-center justify-content-center justify-content-lg-start">
            <router-link to="/" class="nav-link text-white" style="text-decoration: none; color: white;">Home</router-link>
            <router-link to="/products/create" class="nav-link text-white" style="text-decoration: none; color: white;">Add Product</router-link>
          </div>
        </div>
      </div>
    </header>
  
    <div class="card">
      <div class="card-body">
        <div class="container-fluid">
          <router-view></router-view>
        </div>
      </div>
    </div>
  
  </div>
  
</template>
  
<script>
  export default {
    name: 'App'
  }
</script>