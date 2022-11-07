<script setup>
import { RouterLink, RouterView } from 'vue-router'


</script>

<template>
  <header>
        <div class="slideshow-container">
                <div class="mySlides fade">
                    <div class="numbertext">1 / 3</div>
                    <img class="img-slider" src="../src/assets/img/RYM1.jpg" style="width:100%">
             </div>
             <div class="mySlides fade">
                    <div class="numbertext">2 / 3</div>
                    <img class="img-slider"  src="../src/assets/img/RYM12.jpg" style="width:100%">   
             </div>
             <div class="mySlides fade">
                    <div class="numbertext">3 / 3</div>
                    <img  class="img-slider"  src="../src/assets/img/RYM13.jpg" style="width:100%">
             </div>
            </div>
      </header>

  <RouterView />
</template>

<style scoped>

.slideshow-container {
  max-width: 100%;
  position: relative;
  margin: auto;
}
body {
  width: 100%;
}

.prev,
.next {
  cursor: pointer;
  position: absolute;
  top: 50%;
  width: auto;
  margin-top: -22px;
  padding: 16px;
  color: white;
  font-weight: bold;
  font-size: 18px;
  transition: 0.6s ease;
  border-radius: 0 3px 3px 0;
}

.next {
  right: 0;
  border-radius: 3px 0 0 3px;
}

.prev:hover,
.next:hover {
  background-color: rgba(0, 0, 0, 0.8);
}

.text {
  color: #f2f2f2;
  font-size: 15px;
  padding: 8px 12px;
  position: absolute;
  bottom: 8px;
  width: 100%;
  text-align: center;
}

.numbertext {
  color: #f2f2f2;
  font-size: 12px;
  padding: 8px 12px;
  position: absolute;
  top: 0;
}
.fade {
  -webkit-animation-name: fade;
  -webkit-animation-duration: 1.5s;
  animation-name: fade;
  animation-duration: 1.5s;
}

@-webkit-keyframes fade {
  from {
    opacity: 0.4;
  }
  to {
    opacity: 1;
  }
}

@keyframes fade {
  from {
    opacity: 0.4;
  }
  to {
    opacity: 1;
  }
}
img.img-slider {
  height: 35rem;
}
</style>
