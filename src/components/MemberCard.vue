<template>
  <div class="member-card" @click="turn">
    <div class="front" :class="frontTurn">
      <img :src="image">
      <div class="infobox">
        <h2 class="name">{{ member.name }}</h2>
        <h2 class="name">{{ member.surname }}</h2>
        <br>
        <p>{{ member.role }}</p>
        <br>
        <p>AGE: {{ member.age }}</p>
        <p>MISSIONS: {{ member.missions }}</p>
      </div>
    </div>

    <div class="back" :class="backTurn">
      <h4>{{ member.name }}'S FAMOUS QOUTE:</h4>
      <p v-html="member.qoute"></p>
    </div>
  </div>
</template>
<script>
export default {
  name: 'Member',

  data:()=>({
    frontTurn: '',
    backTurn: '',
    turned: false
  }),

  computed:{
    image(){
      return require(`@/assets/team/${this.member.image}.jpg`)
    }
  },

  props: {
    member: {
      type: Object,
      default: () => ({
        image: null,
        name: 'Unkown',
        surname:  'Unkown',
        role:  'Unkown',
        age: 0,
        missions: 0,
        qoute:  'Unkown',
      })
    }
  },
  methods:{
    turn(){
      if(!this.turned){
        this.frontTurn = 'front-turn'
        this.backTurn = 'back-turn'
        this.turned = true;
      }
      else{
        this.frontTurn = ''
        this.backTurn = ''
        this.turned = false
      }
    }
  }
}
</script>
<style>

.member-card{
  width: 300px;
  position: relative;
  cursor: pointer;
}

.front{
  background: rgb(0, 0, 0);
  background: linear-gradient(90deg, rgba(0, 0, 0, 0.05) 15%, rgba(119, 119, 119, 0.05) 46%, rgba(255, 255, 255, 0.05) 63%);
  border-radius: 0.3rem;
  display: flex;
  flex-direction: row;
  backface-visibility: hidden;
  transition: all 0.8s ease;
  perspective: 50rem;
  width: 100%;
}
.front img{
  width: 50% !important;
  border-radius: 0.3rem;
  height: auto;
}

.infobox{
  text-align: left;
  margin-top: 1vh;
  margin-left: 3vh;
  width: 50%;
}

.infobox h2{
  font-size: 1.2rem!important;
  margin: 0!important;
  padding: 0!important;
}

.infobox p{
  font-size: 0.7rem!important;
  margin: 0!important;
  padding: 0!important;
  font-style: normal;
}

.back{
  background: rgb(14,17,20);
  background: linear-gradient(-135deg, rgba(14,17,20,1) 0%, rgba(31,38,45,1) 100%);
  text-align: center;
  top: 0;
  width: 100%;
  height: 100%;
  position: absolute;
  border-radius: 0.3rem;
  backface-visibility: hidden;
  transition: all 0.8s ease;
  transform: rotateY(-180deg);
  perspective: 50rem;
  padding-top: 1rem;
}

.back h4{
  font-size: 1rem;
  padding-top: 2vh;
  font-weight: bold;
  color: #484d52;
}

.back p{
  font-size: 3vw !important;
  font-family:Merriweather-LightItalic,sans-serif !important;
  color: #dfdfe1;
}

.front-turn{
  transform: rotateY(180deg);
}

.back-turn{
  transform: rotateY(0deg);
}

@media (min-width: 600px){
  .member-card{
    width: 600px;
  }
  .member-card h2{
    font-size: 2rem!important;
  }
  .member-card p{
    font-size: 0.8rem!important;
  }
  .infobox{
    position: absolute;
    top: 50%;
    left: 80%;
    transform: translate(-50%, -50%);
    margin: 0;
  }

  .back p{
    font-size: 1.5rem !important;
    margin-top: 3rem;
  }
}

@media (min-width: 1200px) {
  .member-card{
    width: 30%;
  }

  .infobox h2{
    font-size: 1.2rem !important;
  }

  .infobox p{
    font-size: 0.7rem !important;
  }

  .back h4{
    font-size: 1rem !important;
  }
  .back p{
    font-size: 1.2rem !important;
    margin-top: 1rem;
  }
}

@media(min-width: 1600px){
  .infobox h2{
    font-size: 1.5rem !important;
  }
  .infobox p{
    font-size: 1rem!important;
  }
}

</style>