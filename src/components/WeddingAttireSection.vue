<template>
  <div class="p-5" id="weddingAttireSection">
    <div class="container">
      <div class="row justify-content-center">
        <div class="col-md-6">
          <h2 class="display-2 text-center">Wedding Attire</h2>
          <p class="text-center">We kindly encourage our guests to dress in our color palette on our special day</p>
          <div class="d-flex justify-content-center">
            <div
                v-for="color in colors"
                :key="color"
                @click="changeColor($event, color)"
                :style="{ backgroundColor: color }"
                :class="['color-circle', 'me-lg-2', 'me-xs-0', currentColor === color ? 'active' : '']">
            </div>
          </div>
          <div class="text-center mt-3">
            <div class="d-inline-block">
              <svg :fill="currentColor" height="100px" version="1.1" id="Layer_1"
                   xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"
                   viewBox="0 0 512 512" xml:space="preserve">
              <g>
                <g>
                  <path d="M256,231.487c-31.925,34.815-84.599,31.583-86.226,31.583c0,10.664,0,229.397,0,243.104c0,3.218,2.609,5.827,5.827,5.827
                    h42.595c2.875,0,5.32-2.097,5.759-4.939l32.023-207.634l32.023,207.634c0.438,2.842,2.883,4.939,5.759,4.939h42.595
                    c3.218,0,5.827-2.609,5.827-5.827l0.034-243.101C340.334,263.073,289.037,266.673,256,231.487z"/>
                </g>
              </g>
                <g>
                <g>
                  <path d="M256.182,17.509c-8.372,0-15.985-3.208-21.705-8.45C242.29,22.341,248.467,32.84,256,45.645
                    c10.991-18.682,10.056-17.094,21.128-35.915C271.501,14.572,264.189,17.509,256.182,17.509z"/>
                </g>
              </g>
                <g>
                <g>
                  <path d="M335.586,209.832v-16.354h44.335v-0.001V52.781c0-24.41-19.772-44.336-44.336-44.336v0.239
                    c-5.536-1.712-21.473-6.64-28.084-8.684l-11.89,43.571l-23.258,4.361l5.945,22.69l-29.203,74.339V109.81L233.7,70.624l5.945-22.69
                    l-23.258-4.361L204.499,0l-28.085,8.684V8.445c-24.486,0-44.336,19.848-44.336,44.336v140.697h44.335v16.354h-44.335v25.983
                    c0,3.01,2.441,5.451,5.451,5.451h33.434c3.015,0,5.451-2.444,5.451-5.451c0,3.011,2.441,5.451,5.451,5.451
                    c54.755,0,74.135-48.309,74.135-48.309c12.7,28.723,41.405,48.309,74.135,48.309c3.01,0,5.451-2.44,5.451-5.451
                    c0,3.008,2.438,5.451,5.451,5.451h33.434c3.01,0,5.451-2.44,5.451-5.451v-25.983H335.586z M321.413,106.906H292.34V90.554h29.073
                    V106.906z"/>
                </g>
              </g>
              </svg>
            </div>
            <div class="d-inline-block">
              <svg :fill="currentColor" version="1.1" id="Capa_1" xmlns="http://www.w3.org/2000/svg"
                   xmlns:xlink="http://www.w3.org/1999/xlink"
                   viewBox="0 0 273.414 273.414" xml:space="preserve" height="100px">
              <g>
                <path d="M88.033,54.724c-0.041,9.849-1.027,19.573-2.917,29.108h28.758v-6.25c0-4.143,3.357-7.5,7.5-7.5h31
                  c4.143,0,7.5,3.357,7.5,7.5v6.25h28.456c-1.902-9.576-2.905-19.33-2.948-29.107c7.98-4.853,13.279-13.361,13.279-23.05
                  C198.661,16.586,192.247,0,185.082,0c-12.692,0-33.154,17.571-40.769,32.318c-0.979,1.895-2.939,3.091-5.072,3.091h-5.056
                  c-2.135,0-4.092-1.194-5.072-3.091C121.497,17.571,101.03,0,88.333,0c-7.171,0-13.58,16.586-13.58,31.674
                  C74.753,41.363,80.052,49.87,88.033,54.724z"/>
                <path d="M199.307,117.894c-2.825-6.19-5.235-12.562-7.218-19.062h-32.215v6.25c0,4.143-3.357,7.5-7.5,7.5h-31
                  c-4.143,0-7.5-3.357-7.5-7.5v-6.25H81.351c-1.981,6.471-4.396,12.833-7.238,19.063c-16.165,35.431-18.447,90.91-19.034,145.334
                  c-0.029,2.691,1.02,5.281,2.912,7.194c1.892,1.913,4.472,2.991,7.163,2.991h143.109c2.691,0,5.271-1.077,7.163-2.99
                  c1.893-1.913,2.941-4.504,2.911-7.195C217.75,208.804,215.476,153.325,199.307,117.894z"/>
                <rect x="128.874" y="85.082" width="16" height="12.5"/>
              </g>
            </svg>
            </div>
            <p class="mt-4 fw-bold">Semi-formal Attire</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      colors: ['#020645', '#111ca9', '#6503ca', '#b88de7', '#ddd0c7'],
      currentColor: '#020645'
    }
  },
  methods: {
    changeColor(event, color) {
      this.currentColor = color;
    }
  }
}
</script>
<style scoped>
#weddingAttireSection {
  background-color: #fbf9fe;
}

.color-circle {
  width: 50px;
  height: 50px;
  border-radius: 50%;
  cursor: pointer;
}

.active {
  border: 5px solid #ccc;
}
</style>