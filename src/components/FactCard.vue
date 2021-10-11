<template>
  <div class="fact-card">
    <img :src="factImage">
    <h2>{{fact.title}}</h2>
    <p v-html="fact.desc"></p>
  </div>
</template>
<script>
export default {
  name: 'FactCard',
  props:{
    fact: {
      type: Object,
      default: () =>( {
          title: 'Unkown',
          desc: 'Unkown',
          image: null
      })
    },
  },
  computed: {
    factImage() {
      if (this.fact.image) {
        return require(`@/assets/icons/${this.fact.image}.svg`)
      }else{
        return ''
      }

    }
  }
}
</script>
<style>
.fact-card{
  background-color: #fdfdff;
  color: #161b20;
  width: 28rem;
  transition: linear 0.1s;
}

.fact-card:hover{
  -webkit-box-shadow: 0 0 15px -9px #000000;
  box-shadow: 0 0 15px -9px #000000;
  transition: linear 0.1s;
}

.fact-card img{
  background-color: #ffdc08;
  width: 60px;
  height: 60px;
  padding: 0.5rem;
  border-radius: 5rem;
  position: relative;
  margin-top: -2.5rem;
}

.fact-card h2{
  font-size: 24px !important;
  margin-top: 2.5rem !important;
  margin-bottom: 2.5rem;
}

.fact-card p{
  font-size: 14px!important;
  width: 80%;
  letter-spacing: 1px;
  line-height: 1.5rem;
  margin: 0 auto 5rem;
}

/*Mobile*/
@media (max-width: 600px) {
  .fact-card{
    margin-bottom: 4rem;
  }
  .fact-card p{
    padding-bottom: 3rem;
    letter-spacing: normal;
    width: 90% !important;
    font-size: 4vw!important;
  }
}

/*Tablet*/
@media (min-width: 600px) {
  .fact-card{
    width: 60%;
    margin-bottom: 5rem;
  }
  .fact-card p{
    font-size: 1.8vw !important;
    width: 90%;
  }
}
/*Desktops*/
@media (min-width: 1200px) {
  .fact-card{
    width: 30%;
  }

  .fact-card p{
    font-size: 0.8vw !important;
    width: 80%;
  }
}
/*Big destkops*/
@media (min-width: 1800px) {
  .fact-card{
    width: 28rem;
  }

  .fact-card p{
    font-size: 0.8vw !important;
    width: 80%;
  }
}
</style>