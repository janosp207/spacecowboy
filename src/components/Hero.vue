<template>
  <div class="hero" id="about">
    <div class="hero_wrap">
      <h1>HEY THERE, WE ARE</h1>
      <h1>SPACECOWBOY</h1>
      <h2>- AN INDEPENDENT SPACE AGENCY -</h2>
      <button class="button" type="button" @click="scrollToAbout()">LEARN MORE</button>
    </div>
  </div>
</template>
<script>
export default {
  name: 'Hero',
  methods:{
    scrollToAbout(){
      let el = document.getElementById('fact')
      el.scrollIntoView({behavior: 'smooth'})
    }
  }
}
</script>
<style>
.hero{
  width: 100%;
  height: 100vh;
  background-color: #161b20;
  background-repeat: no-repeat;
  background-size: cover;
  background-image: url("../assets/bgdesktop.jpg");
}

.hero_wrap{
  width: 75%;
  text-align: center;
  color: #ffffff;
  position: relative;
  top: 55%;
  left: 50%;
  -ms-transform: translate(-50%, -50%);
  transform: translate(-50%, -50%);
  font-family: Montserrat-Bold, sans-serif;

}

.hero_wrap h1{
  margin: 0;
  font-size: 3vw;
  letter-spacing: 3px;
}

.hero_wrap h2{
  font-size: 2vw;
  margin-bottom: 6rem;
  margin-top: 3rem;
  letter-spacing: 3px;
}

.button{
  background: rgb(255,230,10);
  background: linear-gradient(180deg, rgba(255,230,10,1) 0%, rgba(255,221,7,1) 10%, rgba(255,212,6,1) 50%, rgba(255,203,5,1) 90%, rgba(255,200,4,1) 100%);
  font-size: 18px;
  color: #161b20;
  padding: 1.2rem 5rem 1.1rem;
  margin-top: 2rem;
  border: none;
  border-radius: 0.2rem;
  z-index: 2;
  cursor: pointer;
}

.button:hover{
  background: linear-gradient(180deg, rgba(255, 240, 10,1) 0%, rgb(255, 231, 7) 10%, rgba(255,222,6,1) 50%, rgba(255,213,5,1) 90%, rgba(255,210,4,1) 100%);
}

/*Tablet*/
@media (min-width: 600px) {
  .hero{
    background-position-x: 35%;
  }

  .hero_wrap h1{
    font-size: 5vw;
  }

  .hero_wrap h2{
    font-size: 3vw;
  }
}

@media (max-width: 800px) {

  .hero{
    background-image: url("../assets/bg-mobile.jpg");
    background-position-x: 40%;
  }
  .hero_wrap{
    width: 100%;
    background-position-x: center;
  }

  .hero_wrap h1{
    font-size: 9vw;
    width: 70%;
    margin: 0 auto;
  }
  .hero_wrap h2{
    font-size: 4vw;
    letter-spacing: 0;
    margin-top: 1.5rem;
  }

  .button{
    width: 50%;
    font-size: 4vw;
    text-align: center;
    padding: 0.7rem 0;
    margin-top: 0;
  }
}

@media (min-width: 1800px) {
  .hero_wrap h1{
    font-size: 3vw;
  }
  .hero_wrap h2{
    font-size: 1.8vw;
  }
}
</style>