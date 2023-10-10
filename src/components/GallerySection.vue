<template>
  <div class="py-5" id="gallerySection">
    <div class="container">
      <div class="gallery-grid">
        <div v-for="(image, index) in galleryImages" :key="index" class="img-cell">
          <img :src="image.path" @click="openImage(index)" alt="Gallery Image" class="img-fluid">
        </div>
      </div>
    </div>
  </div>

  <div v-if="lightboxOpen" class="lightbox-overlay">
    <span class="close" @click="lightboxOpen = false">X</span>
    <img :src="galleryImages[currentImage].path" class="lightbox-img">
    <a class="text-decoration-none prev" @click="previousImage">&#10094;</a>
    <a class="text-decoration-none next" @click="nextImage">&#10095;</a>
  </div>
</template>

<script>
import image1 from "@/assets/gallery/1.jpg";
import image2 from "@/assets/gallery/2.jpg";
import image3 from "@/assets/gallery/3.jpg";
import image4 from "@/assets/gallery/4.jpg";
import image5 from "@/assets/gallery/5.jpg";
import image6 from "@/assets/gallery/6.jpg";
import image7 from "@/assets/gallery/7.jpg";
import image8 from "@/assets/gallery/8.jpg";
import image9 from "@/assets/gallery/9.jpg";
import image10 from "@/assets/gallery/10.jpg";
import image11 from "@/assets/gallery/11.jpg";

export default {
  data() {
    return {
      lightboxOpen: false,
      currentImage: 0,
      galleryImages: [
        {path: image1},
        {path: image2},
        {path: image3},
        {path: image4},
        {path: image5},
        {path: image6},
        {path: image7},
        {path: image8},
        {path: image9},
        {path: image10},
        {path: image11}
      ],
    }
  },
  mounted() {
    document.addEventListener('keydown', this.handleKeydown);
  },
  beforeUnmount() {
    document.removeEventListener('keydown', this.handleKeydown);
  },
  methods: {
    openImage(index) {
      this.currentImage = index;
      this.lightboxOpen = true;
    },
    nextImage() {
      this.currentImage = (this.currentImage + 1) % this.galleryImages.length;
    },
    previousImage() {
      this.currentImage = (this.currentImage - 1 + this.galleryImages.length) % this.galleryImages.length;
    },
    handleKeydown(event) {
      if (event.key === "Escape" || event.keyCode === 27) {
        this.lightboxOpen = false;
      }
    }
  }
}
</script>
<style scoped>
.gallery-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 5px;
}

.img-cell {
  overflow: hidden;
}

.img-cell img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.3s;
  cursor: pointer;
}

.img-cell:hover img {
  transform: scale(1.1);
}

.lightbox-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(0, 0, 0, 0.9);
  z-index: 1000;
  display: flex;
  justify-content: center;
  align-items: center;
}

.lightbox-img {
  max-width: 80%;
  max-height: 80%;
  margin: 0 auto;
}

.close, .prev, .next {
  position: absolute;
  color: white;
  cursor: pointer;
  font-size: 2rem;
}

.close {
  top: 2%;
  right: 2%;
}

.prev {
  top: 50%;
  left: 2%;
  transform: translateY(-50%);
}

.next {
  top: 50%;
  right: 2%;
  transform: translateY(-50%);
}
</style>