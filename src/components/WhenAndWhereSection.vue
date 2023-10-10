<template>
  <div class="text-center py-5" id="whenAndWhereSection">
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
  </div>
</template>
<script>

</script>
<style scoped>
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
  background: rgba(128, 0, 128, 0.5);
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
</style>