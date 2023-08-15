<template>
  <div class="full-screen-image d-flex flex-column align-items-center justify-content-center text-center text-white">
    <p class="drop-in">November 14, 2023</p>
    <h1 class="drop-in">Noel and Claire's Wedding</h1>
    <p class="drop-in">{{ days }} Days {{ hours }} Hours {{ minutes }} Minutes {{ seconds }}</p>
    <p class="drop-in"></p>
  </div>
  <section class="text-center py-5">
    <div class="container">
      <i class="big fas fa-church"></i>
      <p class="big">Chapel on the hill church @ 2pm</p>
      <p class="slight-big">Don Bosco Batulao, Brgy. Cahil, Calaca Batangas, Tagaytay, Batangas</p>
      <br>
      <i class="big fas fa-map-marker-alt"></i>
      <p class="big">Hacienda Solange Tagaytay @ 5pm</p>
      <p class="slight-big">Brgy, 047 Aguinaldo - Alfonso Rd, Alfonso, 4123 Cavite</p>
    </div>
  </section>
</template>
<script>
export default {
  data() {
    return {
      days: 0,
      hours: 0,
      minutes: 0,
      seconds: 0,
    };
  },
  mounted() {
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


.full-screen-image p:nth-child(1) { animation-delay: 0.5s; }
.full-screen-image h1 { animation-delay: 0.7s; }
.full-screen-image p.countdown { animation-delay: 0.8s; }
.full-screen-image p:nth-child(3) { animation-delay: 0.9s; }

.big {
  font-size: 2.5rem;
}

.slight-big {
  font-size: 1.2rem;
}
</style>