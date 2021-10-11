<template>
  <div id="contact" class="contact-container">
    <h2>SAY HELLO</h2>
    <p>Got some questions about us? Wanna do business with us? <br>Or do you just want to send us your latest cat-content - there you go:
    </p>
    <div class="contact-wrapper">
      <div class="inputs" >
        <div class="input" :class="cfname">
          <label for="fname" v-if="cfname==='incorrect'">Sorry, that's no valid last name</label><br>
          <input id="fname" placeholder="First Name" type="text" v-model="fname" @click="reset($event)">
          <img v-if="cfname==='correct'" src="../assets/icons/correct.png">
          <img v-if="cfname==='incorrect'" src="../assets/icons/wrong.png">
        </div>

        <div class="input" :class="clname">
          <label for="lname" v-if="cfname==='incorrect'">Sorry, that's no valid last name</label><br>
          <input id="lname" placeholder="Last Name" type="text" v-model="lname" @click="reset($event)">
          <img v-if="clname==='correct'" src="../assets/icons/correct.png">
          <img v-if="clname==='incorrect'" src="../assets/icons/wrong.png">
        </div>

        <div class="input" :class="cemail">
          <label for="email" v-if="cemail==='incorrect'">Sorry, that's no valid E-Mail address</label><br>
          <input id="email" placeholder="E-mail" type="email" v-model="email" @click="reset($event)">
          <img v-if="cemail==='correct'" src="../assets/icons/correct.png">
          <img v-if="cemail==='incorrect'" src="../assets/icons/wrong.png">
        </div>
      </div>
        <textarea id="text" placeholder="Your Message"></textarea>
    </div>
    <button class="button" @click="sendEmail">SEND THAT MAIL</button>
  </div>
</template>
<script>
export default {
  name: 'Contact',
  data: ()=>({
    cfname: '',
    clname: '',
    cemail: '',

    fname: '',
    lname: '',
    email: ''
  }),

  methods:{
    reset(event){
      if(event.currentTarget.id === "fname")
        this.cfname = ''
      else if(event.currentTarget.id === "lname")
        this.clname = ''
      else if(event.currentTarget.id === "email")
        this.cemail = ''
    },

    sendEmail(){
      if(this.fname === '')
        this.cfname = 'incorrect'

      else
        this.cfname = 'correct'

      if(this.lname === '')
        this.clname = 'incorrect'
      else
        this.clname = 'correct'

      if(this.validateEmail(this.email))
        this.cemail = 'correct'
      else
        this.cemail = 'incorrect'
    },

    validateEmail(email) {
        const regex = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
        return regex.test(String(email).toLowerCase());
    }
  }
}

</script>
<style>

  .correct input{
    color: #81c784;
  }

  .incorrect input{
    color: #ef5350;
    border: 2px solid #ef5350;
  }

  .contact-container{
    width: 100%;
    background-color: #acb1b6;
    text-align: center;
    padding-top: 8vh;
    padding-bottom: 20vh;
  }
  .contact-container h2{
    font-family: Montserrat-Bold, sans-serif;
    font-size: 36px;
    font-weight: bold;
  }

  .contact-container p{
    font-family: Merriweather-Light, sans-serif;
    font-size: 18px;
    font-weight: lighter;
    margin: 1.5rem auto 0;
  }

  .contact-wrapper{
    width: 50%;
    display: flex;
    justify-content: center;
    font-size: 0.7vw;
    font-family: Montserrat-Bold, sans-serif;
    gap: 2rem;
    margin: 7rem auto 3vh;
  }

  .inputs{
    width: 50%;
  }

  input{
    padding-left: 1rem;
    padding-top: 0.8rem;
    padding-bottom: 0.8rem;
    background: rgb(231,230,230);
    background: linear-gradient(180deg, rgba(231,230,230,1) 0%, rgba(252,252,252,1) 100%);
    height: 100%;
    border: 2px solid transparent;
    border-radius: 0.3rem;
    width: 100%;
  }

  .input{
    position: relative;
  }

  .input img{
    position: absolute;
    bottom: 10px;
    right: 10px;
  }

  textarea{
    width: 50%;
    margin-top: 1.5rem;
    border-radius: 0.3rem;
    background: rgb(231,230,230);
    background: linear-gradient(180deg, rgba(231,230,230,1) 0%, rgba(252,252,252,1) 100%);
    border: 2px solid transparent;
    resize: none;
    padding: 0.8rem 1rem;
    -webkit-transition: all 0.1s linear;
    -moz-transition: all 0.1s linear;
    -o-transition: all 0.1s linear;
    transition: all 0.1s linear;
  }

  textarea:focus, input:focus{
    outline: none;
    border: 2px solid #a7a7a7;
    -webkit-transition: all 0.1s linear;
    -moz-transition: all 0.1s linear;
    -o-transition: all 0.1s linear;
    transition: all 0.1s linear;
  }

  label{
    text-align: left;
    font-size: 0.6vw;
    font-weight: normal;
    color: #ef5350;
    padding-top: 1rem;
    float: left;
  }

  ::placeholder{
    color: #acb1b6;
  }

  .button{
    font-family: Montserrat-Bold, sans-serif;
  }
  /*Mobile*/
  @media (max-width: 600px) {
    .contact-container p{
      padding-top: 2rem;
      padding-bottom: 2rem;

    }
    .contact-wrapper{
      display: block;
      width: 70%;
      font-size: 4vw;
    }
    .inputs{
      width: 100%;
    }
    textarea{
      width: 100%;
      height: 30vh;
    }

    label{
      font-size: 0.8rem;
    }
  }
  /*Tablet*/
  @media (min-width: 600px) {
    .contact-wrapper{
      width: 80%;
      font-size: 1rem;
    }
    label{
      font-size: 0.8rem;
    }
  }
  /*Desktop*/
  @media (min-width: 1200px) {
    .contact-wrapper{
      margin-top: 3rem;
      width: 40%;
      font-size: 1rem;
    }
  }
  /*Big desktop*/
  @media (min-width: 1800px) {
    .contact-wrapper{
      margin-top: 3rem;
      width: 30%;
      font-size: 1rem;
    }
  }
</style>