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
                @click="changeColor(color)"
                :style="{ backgroundColor: color }"
                class="color-circle mr-2">
            </div>
          </div>
          <div class="text-center mt-3">
            <i class="fas fa-user-tie" :style="{ color: currentColor }"/>
            &nbsp;
            <i class="fas fa-dress" :style="{ color: currentColor }"/>
            <p class="mt-2">Semi-formal Attire</p>
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
    changeColor(color) {
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
  border: 2px solid #fff;
  margin-right: 10px;
}
</style>