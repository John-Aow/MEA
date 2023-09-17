<template>
  <MainView />
</template>

<style>
.bg-mea{
  background-color: #FE5000 !important;
}
.bg-mea-light{
  background-color: #fddfd1 !important;
}
.color-mea{
  color: #FE5000 !important;
}
.color-mea-light{
  color: #fddfd1 !important;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

@font-face {
  font-family: "Ozone";
  src: local("Merienda"),
   url(../src/assets/fonts/DB\ Ozone\ X.ttf) format("truetype");
}


</style>

<script>
// @ is an alias to /src
import MainView from '@/views/MainView.vue'
export default {
  components: {
    MainView
  }
}
</script>
