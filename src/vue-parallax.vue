<template>
  <div class="parallax__container" ref="container">
    <div
      class="parallax__image"
      ref="image"
      :style="{
        backgroundImage: `url(${image})`,
        height: imageHeight
      }"
    ></div>
    <div class="parallax__slot">
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    image: { type: String, required: true },
    intensity: { type: Number, default: 15 }
  },
  data() {
    return {
      el: null,
      conatiner: null,
      imageHeight: 0,
      defaultHeight: 360
    };
  },
  mounted() {
    // Extract the height from the style property of the container
    let h = Number(window.getComputedStyle(this.$el).height.replace("px", ""));
    if (!h) {
      this.$refs.container.style.height = this.defaultHeight + "px";
      h = this.defaultHeight;
    }
    /* eslint-disable no-console */
    this.el = this.$refs.image;
    this.container = this.$refs.container;
    this.imageHeight = this.getHeight(h) + "px";
    setTimeout(() => {
      this.animationTrigger(false); // trigger to correct but without animationRequest
    }, 25);

    window.addEventListener("scroll", this.animationTrigger);
  },
  destroyed() {
    window.removeEventListener("scroll", this.animationTrigger);
  },
  methods: {
    animationTrigger(animationRequest = true) {
      const vpo = this.container.getBoundingClientRect();
      const animate = () => {
        if (
          vpo.top < window.innerHeight &&
          vpo.top * -1 < this.container.offsetHeight
        ) {
          // only animate when in range of window
          this.el.style.transform = `translateY(${vpo.top /
            this.getIntensity()}px)`;
        }
      };
      if (animationRequest) {
        window.requestAnimationFrame(() => {
          animate();
        });
      } else {
        animate();
      }
    },
    getIntensity() {
      const intensity = 21 - this.intensity;
      if (intensity <= 1) {
        return -2;
      }
      if (intensity >= 20) {
        return -19;
      }
      return intensity * -1;
    },
    getHeight(h) {
      const docOffset =
        this.container.getBoundingClientRect().top +
        document.documentElement.scrollTop;
      const divider = this.getIntensity() * -1;
      const sum = (window.innerHeight - docOffset) / divider;
      const correction = sum < 1 ? 0 : sum; // set a correction based on the document offset
      return h + window.innerHeight / divider - correction;
    }
  }
};
</script>
<style>
.parallax__container {
  width: 100%;
  position: relative;
  overflow: hidden;
  backface-visibility: hidden;
}
.parallax__image {
  width: 100%;
  position: absolute;
  background-size: cover;
  background-position: 50% 50%;
  left: 0;
}
.parallax__slot {
  position: absolute;
  left: 0;
  right: 0;
  bottom: 0;
  top: 0;
  z-index: 2;
}
</style>
