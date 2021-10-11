<template>
  <div id="app" data-spy="scroll" data-target="#navigation" data-offset="0">
    <Navigation />
    <Hero/>
    <Content/>
    <Footer />
  </div>
</template>

<script>
import Navigation from './components/Navigation.vue'
import Hero from './components/Hero.vue'
import Content from './components/Content.vue'
import Footer from './components/Footer.vue'

export default {
  name: 'App',
  components: {
    Navigation,
    Hero,
    Content,
    Footer
  },
}
</script>

<style>
@font-face {
  font-family: "Merriweather-Light";
  src: local("Merriweather-light"),
  url(./fonts/Merriweather-Light.ttf) format("truetype");
}

@font-face {
  font-family: "Merriweather-LightItalic";
  src: local("Merriweather-LightItalic"),
  url(./fonts/Merriweather-LightItalic.ttf) format("truetype");
}


@font-face {
  font-family: "Montserrat-Regular";
  src: local("Montserrat-Regular"),
  url(./fonts/Montserrat-Regular.ttf) format("truetype");
}

@font-face {
  font-family: "Montserrat-Bold";
  src: local("Montserrat-Bold"),
  url(./fonts/Montserrat-Bold.ttf) format("truetype");
}


#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  font-size: 10px;
  margin: 0;
  padding: 0;
  overflow-y: scroll;
  max-width: 100%;
  height: 100%;
}

.scroll{
  background-color: #484d52;
}
body{
  margin:0;
  padding: 0;
  position: relative;
  overflow-y: scroll;
}
</style>
