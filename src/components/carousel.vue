<template>
  <div>
    <transition-group name="fade" tag="div">
      <div v-for="i in [currentIndex]" :key="i">
        <cld-image :public-id="currentImg"></cld-image>
      </div>
    </transition-group>
  </div>
</template>
<script>
export default {
  name: "Slider",
  data() {
    return {
      images: [
       "v1637784687/store/carousel8_fstjay",
       "v1637784687/store/carousel3_vke2hj",
       "v1637784687/store/carousel5_oaiwht",
       "v1637784687/store/carousel7_ocjkzc",
       "v1637784687/store/crousel4_cnv8uf",
      ],
      timer: null,
      currentIndex: 0
    };
  },

  mounted: function() {
    this.startSlide();
  },

  methods: {
    startSlide: function() {
      this.timer = setInterval(this.next, 4000);
    },
    next: function() {
      this.currentIndex += 1;
    },
    prev: function() {
      this.currentIndex -= 1;
    }
  },

  computed: {
    currentImg: function() {
      return this.images[Math.abs(this.currentIndex) % this.images.length];
    }
  }
};
</script>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: all 0.9s ease;
  overflow: hidden;
  visibility: visible;
  position: absolute;
  width:100%;
  opacity: 1;
}

.fade-enter,
.fade-leave-to {
  visibility: hidden;
  width:100%;
  opacity: 0;
}

img {
  height:600px;
}
</style>