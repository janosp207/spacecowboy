<template>
  <div class="body-container">
     <div class="facts-container" id="fact">
       <h2>A FEW FACTS ABOUT US</h2>
       <p>Before you do business with us, <br>you might want to know a little bit more about our company:</p>
       <div class="wrapper">
         <FactCard v-for="(fact, index) in facts" :key="index+fact.image" :fact="fact"/>
       </div>
     </div>

    <div class="team-container" id="team">
      <h2>THE TEAM</h2>
      <p style="margin-top: 1.5rem;">Yep, that‘s us. Six fine fellows, eager to get on the next adventure. <br>Click on the pictures to get some more information!
      </p>
      <div class="wrapper team">
        <MemberCard v-for="(member, index) in members" :key="index+member.image" :member="member"/>
      </div>
      <Carousel class="carousel" :items="1" center :stagePadding="20" :margin="20" autoWidth >
        <MemberCard v-for="(member, index) in members" :key="index+member.image" :member="member"/>
        <template slot="next"><span class="controls next"><img src="../assets/icons/controls.png"></span></template>
        <template slot="prev"><span class="controls prev"><img src="../assets/icons/controls.png"></span></template>
      </Carousel>
    </div>

    <div class="impresions-container" id="imp">
      <h2>LOOK AT ALL THOSE STARS</h2>
      <p>Some impressions from our trips to frickin outer space, enjoy!</p>
      <div class="wrapper impressions">
          <img class="impressions-image" v-for="(photo,index) in photos" :key="index + photo" :src="require(`@/assets/impressions/${photo.image}.jpg`)" @click="openImage(photo)">
      </div>
      <div class="gallery" v-if="visible">
        <span class="close" @click="closeImage()"><img src="../assets/icons/close.png"></span>
        <img class="big-image" :src="require(`@/assets/impressions/large/${bigImage}large.jpg`)">
        <p class="bigDescription">{{bigDescription}}</p>
        <div class="nextImage" @click="nextImage">
          <img src="../assets/icons/nextImage.png">
          <p>NEXT IMAGE</p>
        </div>
        <div class="prevImage" @click="prevImage">
          <img src="../assets/icons/nextImage.png">
          <p>PREVIOUS IMAGE</p>
        </div>
      </div>
    </div>
    <Contact/>
  </div>
</template>
<script>

import FactCard from "./FactCard"
import Contact from "./Contact"
import MemberCard from "./MemberCard"
import Carousel from 'vue-owl-carousel'

export default {
  name: 'Content',
  components: {
    FactCard,
    Contact,
    MemberCard,
    Carousel
  },
  data:()=>({
    bigImage: '',
    bigDescription: '',
    visible: false,

    facts:[
      {
          image: 'fact1',
          title: 'WE ARE COWBOYS',
          desc: 'You might have guessed that from our company name, but the fact is: <br/>Yes, we are indeed cowboys. Cowboys <br/>who‘d like to go to space. <br/>Deal with it.'
      },

      {
          image: 'fact2',
          title: 'WE LIKE TO TINKER',
          desc: 'There are a lot of things lying around on<br/> a typical Cowboy Ranch. So we started<br/> putting them together, and got really<br/> good at rocket building.'
      },

      {
          image: 'fact3',
          title: 'WE EXPLORE SPACE',
          desc: 'Once we got our first proper rocket,<br/> everything went quite fast. And now we<br/> are the #1 independent space agency in<br/> the world. <br/>Who would have guessed?'
      }
    ],

    members:[
      {
        image: 'cowboy-1',
        name: 'DICK',
        surname: 'HARVEY',
        role: 'CAPTAIN',
        age: 56,
        missions: 13,
        qoute: "„This is a small step for me, <br>but a big step for, like,<br> a small kid“"
      },

      {
        image: 'cowboy-2',
        name: 'RICHIE',
        surname: 'FARHEM',
        role: 'ENGINEER',
        age: 48,
        missions: 13,
        qoute: "„This is a small step for me, <br>but a big step for, like,<br> a small kid“"
      },

      {
        image: 'cowboy-3',
        name: 'JOHN',
        surname: 'SIRACHA',
        role: 'GUNSLINGER',
        age: 47,
        missions: 13,
        qoute: "„This is a small step for me, <br>but a big step for, like,<br> a small kid“"
      },

      {
        image: 'cowboy-4',
        name: 'BERT',
        surname: 'McNAMERA',
        role: 'CAPTAIN',
        age: 56,
        missions: 13,
        qoute: "„This is a small step for me, <br>but a big step for, like,<br> a small kid“"
      },

      {
        image: 'cowboy-5',
        name: 'AL',
        surname: 'SVERINGE',
        role: 'CEO',
        age: 76,
        missions: 13,
        qoute: "„This is a small step for me, <br>but a big step for, like,<br> a small kid“"
      }
    ],

    photos:[
      {
        image: '1',
        description: 'Well, this was amazing!'
      },
      {
        image: '2',
        description: 'Well, this was amazing!'
      },
      {
        image: '3',
        description: 'Well, this was amazing!'
      },
      {
        image: '4',
        description: 'Well, this was amazing!'
      },
      {
        image: '5',
        description: 'Well, this was amazing!'
      },
      {
        image: '6',
        description: 'Well, this was amazing!'
      },
      {
        image: '7',
        description: 'Well, this was amazing!'
      },
      {
        image: '8',
        description: 'Well, this was amazing!'
      },
      {
        image: '9',
        description: 'Well, this was amazing!'
      },
      {
        image: '10',
        description: 'Well, this was amazing!'
      },
      {
        image: '11',
        description: 'Well, this was amazing!'
      },
      {
        image: '12',
        description: 'Well, this was amazing!'
      }
    ]
  }),

  methods:{
    openImage({image, description}){
      this.bigImage=image
      this.bigDescription=description
      this.visible = true
    },

    closeImage(){
      this.bigImage=''
      this.bigDescription=''
      this.visible = false
    },

    nextImage(){
      if(this.bigImage!=12)
        this.bigImage++
    },

    prevImage(){
      if(this.bigImage!=1)
        this.bigImage--
    }
  }
}
</script>
<style>
.carousel{
  position: relative;
  padding-bottom: 10rem;
  margin-top: 1rem;
}

.controls{
  position: absolute;
  bottom: 5.2rem;
  z-index: 5;
  font-size: 1rem;
}

.owl-nav{
  display: none;
}

.owl-dots{
  position: absolute;
  margin-top: 3rem !important;
  left: 50%; /* position the left edge of the element at the middle of the parent */
  transform: translateX(-50%);
}

.owl-dots button span{
  opacity: 30%;
}

.owl-dot .active{
  opacity: 100% !important;
  background: #acb1b6 !important;
}
.next{
  right: 10%;
}

.prev{
  left: 10%;
}

.prev img{
  transform: scaleX(-1);
}
.body-container{
  width: 100%;
}

.body-container h2{
  font-family: Montserrat-Bold, sans-serif;
  font-size: 36px;
  margin-top: 0;
}

.body-container p{
  font-family: Merriweather-Light, sans-serif;
  font-size: 18px;
}

.facts-container{
  background-color: #dfdfe1;
  text-align: center;
  width: 100%;
  color: #161b20;
  padding-top: 8vh;
}
.facts-container p{
  margin-top: 1.5rem;
}

.wrapper{
  width: 75%;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
  margin: 7rem auto 0;
  padding-bottom: 10rem;
}

.team{
  justify-content: center !important;
  gap: 2rem;
}

.team-container{
  text-align: center;
  width: 100%;
  padding-top: 8vh;
  color: #dfdfe1;
  background-image: url("../assets/team-background.jpg");
  background-position: center;
  background-repeat: no-repeat;
  background-size: cover;
}

.team-container .active{
  color: #dfdfe1 !important;
}
.impresions-container{
  background-color: #161b20;
  width: 100%;
  color: #fdfdff;
  text-align: center;
  position: relative;
  padding-top: 8vh;
}

.gallery{
  position: absolute;
  width: 100%;
  height: 100%;
  top:0;
  background-color: rgba(22, 27, 32, 0.95);
}

.close{
  position: absolute;
  top: 20%;
  left: 50%;
  -ms-transform: translate(-50%, -70%);
  transform: translate(-50%, -70%);
  cursor: pointer;
}

.bigDescription{
  position: absolute;
  bottom: 20%;
  left: 50%;
  -ms-transform: translate(-50%, -70%);
  transform: translate(-50%, -70%);
  font-family: Montserrat-Bold, sans-serif !important;
  color: #fdfdff;
}
.nextImage{
  position: absolute;
  top:50%;
  right:5%;
  cursor: pointer;
}

.prevImage{
  position: absolute;
  top: 50%;
  left: 5%;
  cursor: pointer;
}

.prevImage img{
  transform: scaleX(-1);
}

.nextImage p, .prevImage p{
  font-family: Montserrat-Bold, sans-serif;
  font-size: 0.8vw;
  text-align: center;
  margin: 0.5rem !important;
  color: #484d52;
}

.big-image{
  position: absolute;
  top: 50%;
  left: 50%;
  -ms-transform: translate(-50%, -50%);
  transform: translate(-50%, -50%);
}

.impresions-container p{
  margin-top: 1.5rem;
}

.impressions-image{
  height: auto;
  border-radius: 0.5rem;
  margin-bottom: 2vh;
  cursor: pointer;
}

button:focus {outline:0;}
/*Tablet*/
@media (min-width: 600px) {
  .facts-container{
    flex-direction: column;
  }
  .wrapper{
    width: 80%;
    justify-content: center;
  }
  .impressions{
    justify-content: space-between;
  }
  .impressions-image{
    width: 23%;
  }
  .team{
    display: none;
  }
}

/*Desktops*/
@media (min-width: 1200px) {
  .wrapper{
    gap: 2rem;
  }
  .impressions{
    justify-content: space-between;
  }

  .impressions-image{
    width: 12%;
    margin-bottom: 3rem;
  }
  .carousel{
    display: none;
  }
  .team{
    display: flex;
  }
}

/*Big desktops*/
@media (min-width: 1800px) {
  .wrapper{
    width: 75%;
  }

  .impressions-image{
    width: 14%;
  }

}

/*Mobile*/
@media (max-width: 600px) {
  .wrapper{
    padding-bottom: 0;
  }

  .contact-wrapper{
    margin-top: 2rem;
  }

  .body-container p{
    font-size: 4vw;
    width: 70%;
    margin: 0 auto;
  }

  .facts-container{
    margin: 0 auto;
    flex-direction: column;
    padding-bottom: 3rem;
  }

  .wrapper{
    justify-content: center;
    width: 90%
  }

  .body-container h2{
    font-size: 7vw;
  }

  .impressions-image{
    width: 32%;
  }

  .impressions{
    justify-content: space-between;
    padding-bottom: 7rem;
  }

  .impresions-container h2{
    width: 50%;
    margin: 0 auto 2rem;
  }

  .team{
    display: none;
  }

  .big-image{
    width: 100%;
    height: auto;
  }
  .close{
    top: 20%;
  }

  .nextImage{
    display: none;
  }

  .prevImage{
    display: none;
  }
}
</style>