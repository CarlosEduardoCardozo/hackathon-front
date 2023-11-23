  <script setup>
    import { ref } from "vue";

    const toogle = ref(true);


  </script>

<template>
    <div class="teste" :class="{'open': toogle}">
      <button class="burger" @click="toogle = !toogle"></button>
      <div class="menu"> 
        <nav >
          <a href="#" style="animation-delay: 0.2s">About</a>
          <a href="#" style="animation-delay: 0.3s">Portfolio</a>
          <a href="#" style="animation-delay: 0.4s">Services</a>
          <a href="#" style="animation-delay: 0.5s">Contact</a>
        </nav>
      </div>
    </div>
  </template>
  
  
  <style scoped >

@import url('https://fonts.googleapis.com/css2?family=Inter:wght@200&display=swap');

  button {
    border: 0;
    padding: 0;
    background: transparent;
    cursor: pointer;
    color: black;
  }
  
  .burger,
  .menu {
    position: fixed;
  }
  
  .burger {
    z-index: 3;
    top: 0;
    left: 0;
    display: grid;
    place-items: center;
    width: 88px;
    height: 88px;
    background-image: url("./icons/menu.svg");
    background-repeat: no-repeat;
    background-position: center;
  }
  
  body.open .burger {
    background-image: url("./icons/close.svg");
  }
  
  .menu {
    z-index: 2;
    top: 0;
    left: 0;
    display: grid;
    place-items: center;
    width: 250px;
    height: 100%;
    background: #121212;
    translate: -100% 0;
    transition: translate 0.375s cubic-bezier(0.175, 0.885, 0.32, 1);
  }
  
  .menu nav {
    opacity: 0;
  }
  
  @keyframes menu-in {
    0% {
      clip-path: ellipse(60% 60% at 0% 50%);
    }
    100% {
      clip-path: ellipse(120% 120% at 0% 50%);
    }
  }
  
  .open .menu {
    opacity: 1;
    visibility: visible;
    translate: 0;
    animation: menu-in 0.375s;
  }
  
  .open .menu nav {
    opacity: 1;
  }
  
  .menu nav:hover a {
    opacity: 0.25;
  }
  
  .menu nav a:hover {
    opacity: 1;
  }
  
  .menu nav {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
  
  .menu a {
    position: relative;
    color: #f9f9f9;
    font-size: 20px;
    font-family: 'Inter', sans-serif;
    padding: 20px 0;
    width: 190px;
    text-decoration: none;
    transition: 0.4s;
  }
  
  .menu a::before,
  .menu a::after {
    content: "";
    position: absolute;
    left: 0;
    bottom: 10px;
    width: 100%;
    height: 2px;
    border-radius: 2px;
    transition: 0.4s;
  }
  
  .menu a::before {
    opacity: 0;
    background: rgb(255 255 255 / 20%);
  }
  
  .menu a::after {
    transform: scaleX(0);
    transform-origin: 0% 50%;
    background: #f7f7f7;
  }
  
  .menu a:hover::before {
    opacity: 1;
  }
  
  .menu a:hover::after {
    transform: scaleX(1);
  }
  
  body.open .menu a {
    animation: appear 0.25s backwards;
  }
  
  @keyframes appear {
    0% {
      opacity: 0;
      translate: -30px 0;
    }
    100% {
      opacity: 1;
    }
  }
  </style>
  