<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <div class="ccc">{{ message }}</div>
  </div>
</template>

<script>

export default {
  name: 'App',
  components: {
  }, 
  data() {
    return {
      message: "",
      images: [],
      selectedImage: null
    };
  },
  created() {
    this.fetchImages();
  },
  methods: {
    fetchImages() {
      fetch('https://star-fawn.vercel.app/api/good')
        .then(response => response.json())
        .then(data => {
          this.message = data.message;
        })
        .catch(error => {
          console.error('Error fetching images:', error);
        });
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.ccc {
  color: red;
  animation: fadeInScale 1.5s ease-in-out infinite alternate;
}

@keyframes fadeInScale {
  0% {
    opacity: 0.7;
    transform: scale(1);
  }
  100% {
    opacity: 1;
    transform: scale(100);
  }
}
</style>
