<template>
  <div class="container">
    <vue-parallax
      image="https://np-site.s3.amazonaws.com/logos/IMG_1409-1_190404_083401_1.jpg"
      class="test-height"
      :intensity="20"
    >
      cjdhcksd
    </vue-parallax>
    <vue-parallax
      image="https://np-site.s3.amazonaws.com/logos/IMG_1409-1_190404_083401_1.jpg"
    ></vue-parallax>
    <vue-parallax
      image="https://np-site.s3.amazonaws.com/logos/IMG_1409-1_190404_083401_1.jpg"
    ></vue-parallax>
    <vue-parallax
      class="doei"
      image="https://np-site.s3.amazonaws.com/logos/IMG_1409-1_190404_083401_1.jpg"
    ></vue-parallax>
    <vue-parallax
      image="https://np-site.s3.amazonaws.com/logos/IMG_1409-1_190404_083401_1.jpg"
    ></vue-parallax>
    <vue-parallax
      image="https://np-site.s3.amazonaws.com/logos/IMG_1409-1_190404_083401_1.jpg"
    ></vue-parallax>
  </div>
</template>

<script>
import VueParallax from "./vue-parallax";
export default {
  components: { VueParallax }
};
</script>

<style>
.container {
  height: 300vh;
}
.test-height {
  height: 600px;
}
</style>
