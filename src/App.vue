<script setup>
</script>

<template>
 
 <nav class="navbar navbar-expand-lg navbar-dark bg-primary">
  <div class="container-fluid">

    <router-link class="navbar-brand" to="/">
      <img src="https://cdn-icons-png.flaticon.com/512/188/188987.png" alt="Pokevite" width="30" height="24">
    </router-link>

    <router-link class="navbar-brand" to="/">Pokevite</router-link>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNavAltMarkup" aria-controls="navbarNavAltMarkup" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
      <div class="navbar-nav">
        <router-link class="nav-link" aria-current="page" to="/">Home</router-link>
        <router-link class="nav-link" to="/about">About</router-link>
     
      </div>
    </div>
  </div>
</nav>


<div class="main">
  <router-view></router-view>

</div>


<footer class="bg-primary text-light">

    <div>Corporate in {{ new Date().getFullYear() }} by Flávio José</div>

</footer>




</template>

<style>

   body{
    height: 100vh;
    background: rgb(24,121,211); 
    background: linear-gradient(180deg, rgba(24,121,211,1) 0%, rgba(12,75,116,1) 0%, rgba(13,143,255,1) 70%);
   }

    footer{
      position:fixed;
      bottom: 0;
      width: 100%;
      display: flex;
      align-items: center;
      justify-content: center;
      height: 56px;
    
    }

</style>
