<template>
  <div class="container">
    <div class="cube-container">
      <div class="cube" :style="{ animationDuration: `${speed}s` }">
        <div class="face front"></div>
        <div class="face back"></div>
        <div class="face right"></div>
        <div class="face left"></div>
        <div class="face top"></div>
        <div class="face bottom"></div>
      </div>
    </div>

    <div class="controls">
      <label for="speed">Rotation Speed:</label>
      <input
          type="range"
          id="speed"
          v-model="speed"
          min="2"
          max="20"
          step="0.5"
      />
      <span>{{ speed }}s</span>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';

const speed = ref(8);
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
  background-color: #f5f5f5;
  perspective: 1000px;
}

.cube-container {
  width: 200px;
  height: 200px;
  margin: 80px auto;
  perspective: 1000px;
}

.cube {
  width: 100%;
  height: 100%;
  position: relative;
  transform-style: preserve-3d;
  animation: rotate 8s infinite linear;
}

.face {
  position: absolute;
  width: 100%;
  height: 100%;
  opacity: 0.85;
  border: 2px solid rgba(255, 255, 255, 0.5);
}

.front {
  transform: translateZ(100px);
  background: #FF5252; /* Red */
}

.back {
  transform: rotateY(180deg) translateZ(100px);
  background: #4CAF50; /* Green */
}

.right {
  transform: rotateY(90deg) translateZ(100px);
  background: #2196F3; /* Blue */
}

.left {
  transform: rotateY(-90deg) translateZ(100px);
  background: #FFC107; /* Yellow */
}

.top {
  transform: rotateX(90deg) translateZ(100px);
  background: #9C27B0; /* Purple */
}

.bottom {
  transform: rotateX(-90deg) translateZ(100px);
  background: #00BCD4; /* Cyan */
}

@keyframes rotate {
  0% {
    transform: rotateX(0) rotateY(0) rotateZ(0);
  }
  100% {
    transform: rotateX(360deg) rotateY(360deg) rotateZ(360deg);
  }
}

.controls {
  display: flex;
  align-items: center;
  gap: 10px;
  margin-top: 20px;
  padding: 10px 20px;
  background: white;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

input[type="range"] {
  width: 200px;
}

@media (max-width: 768px) {
  .cube-container {
    width: 150px;
    height: 150px;
  }

  .front, .back, .right, .left, .top, .bottom {
    transform-origin: center;
  }

  .front {
    transform: translateZ(75px);
  }

  .back {
    transform: rotateY(180deg) translateZ(75px);
  }

  .right {
    transform: rotateY(90deg) translateZ(75px);
  }

  .left {
    transform: rotateY(-90deg) translateZ(75px);
  }

  .top {
    transform: rotateX(90deg) translateZ(75px);
  }

  .bottom {
    transform: rotateX(-90deg) translateZ(75px);
  }
}
</style>