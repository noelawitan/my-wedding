<template>
  <div class="full-screen-image d-flex flex-column align-items-center justify-content-center text-center text-white">
    <p class="drop-in">November 14, 2023</p>
    <h1 class="drop-in">Noel and Claire's Wedding</h1>
    <p class="drop-in">{{ days }} Days {{ hours }} Hours {{ minutes }} Minutes {{ seconds }} Seconds</p>
    <p class="drop-in"></p>
  </div>
  <section class="p-5">
    <div class="container">
      <div class="row justify-content-center">
        <div class="col-md-6">
          <h2 class="display-2 text-center">Our Story</h2>
          <p class="text-center">
            In a year that challenged the world, our paths miraculously crossed. We soon became friends, sharing endless
            conversations and laughter. As the seasons changed, so did our friendship, blossoming into something deeper
            and more meaningful.
            When the world started to reopen, we began going on magical dates, each one more enchanting than the last.
            Our hearts soon knew that we were made for each other.
          </p>
          <p class="text-center">
            We introduced each other to our families and friends, confirming what we already knew: we were home. We've
            explored new places, tasted new flavors, and built an endless list of memories.
            Noel found creative ways for us to spend quality time together, from surprise getaways to cozy game nights,
            making even the simplest moments unforgettable.
          </p>
        </div>
      </div>
    </div>
  </section>
  <section class="gallery-section py-5">
    <div class="container">
      <div class="gallery-grid">
        <div v-for="(image, index) in galleryImages" :key="index" class="img-cell">
          <img :src="image.path" @click="openImage(index)" alt="Gallery Image" class="img-fluid">
        </div>
      </div>
    </div>
  </section>

  <!-- Lightbox Overlay -->
  <div v-if="lightboxOpen" class="lightbox-overlay">
    <span class="close" @click="lightboxOpen = false">X</span>
    <img :src="galleryImages[currentImage].path" class="lightbox-img">
    <a class="text-decoration-none prev" @click="previousImage">&#10094;</a>
    <a class="text-decoration-none next" @click="nextImage">&#10095;</a>
  </div>
  <section class="text-center py-5">
    <div class="container">
      <div class="row">
        <h2 class="display-2 text-center mb-5">When and Where</h2>
        <!-- Chapel on the Hill -->
        <div class="col-md-6 mb-4 d-flex align-items-stretch">
          <a href="https://maps.app.goo.gl/aXQ1Zb7xW5495zCc8" target="_blank" class="w-100 text-decoration-none">
            <div class="card h-100">
              <div class="card-img-wrapper position-relative">
                <img
                    src="https://2.bp.blogspot.com/-0OzQXeydFww/YFYIIzkrt2I/AAAAAAAAML8/iFsAaLAjM1sYpO3DTWXnYOVX9bVrHMY5gCNcBGAsYHQ/s744/don-bosco-batulao-chapel-on-the-hill.jpg"
                    class="card-img-top img-fixed" alt="Chapel on the Hill">
                <div class="overlay text-center">
                  <p>Click to get the direction</p>
                </div>
              </div>
              <div class="card-body">
                <i class="big fas fa-church"></i>
                <p class="big">Chapel on the hill church @ 2 PM</p>
                <p class="slight-big">Don Bosco Batulao, Brgy. Cahil, Calaca Batangas, Tagaytay, Batangas</p>
              </div>
            </div>
          </a>
        </div>
        <!-- Hacienda Solange -->
        <div class="col-md-6 mb-4 d-flex align-items-stretch">
          <a href="https://maps.app.goo.gl/bb3TekSzjTTsoY4k6" target="_blank" class="w-100 text-decoration-none">
            <div class="card h-100">
              <div class="card-img-wrapper position-relative">
                <img
                    src="https://lh5.googleusercontent.com/p/AF1QipOVJ9a6TTGTunRMjvY9kFZ0RupoQcriZphLdA6h=w480-h270-k-n"
                    class="card-img-top img-fixed" alt="Hacienda Solange">
                <div class="overlay text-center">
                  <p>Click to get the direction</p>
                </div>
              </div>
              <div class="card-body">
                <i class="big fas fa-map-marker-alt"></i>
                <p class="big">Hacienda Solange @ 5 PM</p>
                <p class="slight-big">Brgy, 047 Aguinaldo - Alfonso Rd, Alfonso, 4123 Cavite</p>
              </div>
            </div>
          </a>
        </div>
      </div>
    </div>
  </section>
</template>
<script>
import image1 from '@/assets/gallery/1.jpg';
import image2 from '@/assets/gallery/2.jpg';
import image3 from '@/assets/gallery/3.jpg';
import image4 from '@/assets/gallery/4.jpg';
import image5 from '@/assets/gallery/5.jpg';
import image6 from '@/assets/gallery/6.jpg';
import image7 from '@/assets/gallery/7.jpg';
import image8 from '@/assets/gallery/8.jpg';
import image9 from '@/assets/gallery/9.jpg';
import image10 from '@/assets/gallery/10.jpg';
import image11 from '@/assets/gallery/11.jpg';
export default {
  data() {
    return {
      days: 0,
      hours: 0,
      minutes: 0,
      seconds: 0,
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
      ]
    };
  },
  mounted() {
    document.addEventListener('keydown', this.handleKeydown);
    const weddingDate = new Date('November 14, 2023 14:00:00').getTime();

    setInterval(() => {
      const now = new Date().getTime();
      const distance = weddingDate - now;

      this.days = Math.floor(distance / (1000 * 60 * 60 * 24));
      this.hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
      this.minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
      this.seconds = Math.floor((distance % (1000 * 60)) / 1000);
    }, 1000);
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
@keyframes drop-in {
  0% {
    opacity: 0;
    transform: translateY(-30px);
  }
  100% {
    opacity: 1;
    transform: translateY(0);
  }
}

.full-screen-image {
  background: url('../assets/dashboard-bg.jpg') center center/cover no-repeat fixed;
  width: 100%;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
}

.full-screen-image h1 {
  font-family: 'Great Vibes', cursive;
  font-size: 2.5rem;
  opacity: 0;
  animation: drop-in 1s forwards 0.7s;
}

.full-screen-image p {
  font-size: 1.2rem;
  margin: 0.2rem 0;
  opacity: 0;
  animation: drop-in 1s forwards;
}

.full-screen-image p.countdown {
  font-size: 1rem;
}


.full-screen-image p:nth-child(1) {
  animation-delay: 0.5s;
}

.full-screen-image h1 {
  animation-delay: 0.7s;
}

.full-screen-image p.countdown {
  animation-delay: 0.8s;
}

.full-screen-image p:nth-child(3) {
  animation-delay: 0.9s;
}

.big {
  font-size: 2.5rem;
}

.slight-big {
  font-size: 1.2rem;
}

.card-img-wrapper {
  position: relative;
}

.overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: rgba(128, 0, 128, 0.5); /* Purple background with 50% opacity */
  color: white;
  display: flex;
  justify-content: center;
  align-items: center;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.card-img-wrapper:hover .overlay {
  opacity: 1;
}

/* ... existing styles ... */
.gallery-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
  gap: 5px; /* adjust as needed */
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

/* Lightbox Overlay styles */
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