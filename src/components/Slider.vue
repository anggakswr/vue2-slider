<template>
  <!-- spy lebar 100% kasih container dg width 100% -->
  <div class="slide-container">
    <!-- widthny kecil dan posisiny ditengah -->
    <div class="slide-container2">
      <!-- kasih flex spy nyamping -->
      <div
        class="slide-container3"
        v-bind:style="{ transform: `translateX(${-250 * counter}px)` }"
      >
        <div class="img-slide-div" v-for="image in images" :key="image">
          <img class="img-slide" :src="image" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Slider",
  data() {
    return {
      counter: 0,
      images: [
        "https://upload.wikimedia.org/wikipedia/commons/thumb/b/b6/Image_created_with_a_mobile_phone.png/1200px-Image_created_with_a_mobile_phone.png",
        "https://www.w3schools.com/w3css/img_lights.jpg",
        "https://cdn.pixabay.com/photo/2015/04/23/22/00/tree-736885__340.jpg",
        "https://interactive-examples.mdn.mozilla.net/media/cc0-images/grapefruit-slice-332-332.jpg",
        "https://image.freepik.com/free-photo/double-exposure-image-business-profit-growth_31965-3022.jpg",
      ],
    };
  },
  methods: {
    nextSlide: function() {
      if (this.counter == this.images.length - 1) {
        this.counter = 0;
      } else {
        this.counter++;
      }
    },
  },
  mounted: function() {
    this.$nextTick(function() {
      setInterval(this.nextSlide, 3000);
    });
  },
};
</script>

<style scoped>
.img-slide {
  width: 250px;
}

.slide-container {
  width: 100%;
  overflow: hidden;
}

.slide-container2 {
  width: 250px;
  margin: auto;
}

.slide-container3 {
  display: flex;
  align-items: center;
  transition: 0.5s;
}
</style>
