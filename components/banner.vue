<template>
  <div class="containerBanner">
    <div class="image"></div>
  </div>
</template>

<style scoped>
.containerBanner {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100vw;
}

.image {
  display: flex;
  justify-content: center;
  height: 282px;
  width: 375px;
  background-image: url("../public/assets/images/bannerMobile.png");
  background-repeat: no-repeat;
}

@media (min-width: 1200px) {
  .containerBanner {
    width: auto;
  }

  .image {
    height: 640px;
    width: 480px;
    background-image: url("../public/assets/images/bannerDesktop.png");
    background-size: cover;
  }
}
</style>
