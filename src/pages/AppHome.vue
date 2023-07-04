<template>
    <div class="matrix-background" ref="matrixBackground">
      <div v-for="line in 10">
        <div class="code-container mx-1">
           <div v-for="line in 30"> 
              <div v-for="(line, index) in codeLines" :key="index" class="code-line">
                <div class="code-text">{{ line }}</div>
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
        codeLines: [
          "01001000",
        ],
        animationInterval: null,
      };
    },
    mounted() {
      this.startAnimation();
      window.addEventListener("resize", this.handleResize);
      this.handleResize();
    },
    beforeDestroy() {
      this.stopAnimation();
      window.removeEventListener("resize", this.handleResize);
    },
    methods: {
      startAnimation() {
        this.animationInterval = setInterval(() => {
          this.codeLines.push(this.generateRandomCodeLine());
          this.codeLines.shift();
        }, 200);
      },
      stopAnimation() {
        clearInterval(this.animationInterval);
      },
      generateRandomCodeLine() {
        // Logica per generare una riga di codice casuale
        return Math.random().toString(10).substring(4, 15);
      },
      handleResize() {
        const matrixBackground = this.$refs.matrixBackground;
        matrixBackground.style.height = `${window.innerHeight - 72}px`;
      },
    },
  };
  </script>
  
  <style>
  .matrix-background {
    background-color: black;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    overflow: hidden;
  }
  
  .code-container {
    font-family: 'Courier New', monospace;
    font-size: 16px;
    color: green;
    white-space: nowrap;
    animation: scroll 60s linear infinite;
  }
  
  .code-line {
    padding: 2px 0;
  }
  
  @keyframes scroll {
    0% {
      transform: translateY(0);
    }
    100% {
      transform: translateY(100%);
    }
  }
  </style>
  