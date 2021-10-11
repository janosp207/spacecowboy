<template>
  <nav id="navigation" class="navbar fixed-top navbar-expand-lg navbar-dark" :class="{ 'scroll': !isOnTop}">
      <a class="navbar-brand" href="#">
        <img src="@/assets/icons/Logo.svg">
      </a>
      <button class="navbar-toggler collapsed" type="button" data-toggle="collapse" data-target="#navbarContent" aria-controls="navbarContent" aria-expanded="false" aria-label="Toggle navigation">
      </button>
      <div class="collapse navbar-collapse float-right" id="navbarContent">
        <ul class="navbar-nav ml-auto">
          <li class="nav-item">
            <a class="nav-link" href="#about">ABOUT US</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#team">THE TEAM</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#imp">IMPRESSIONS</a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#contact">CONTACT</a>
          </li>
        </ul>
      </div>
  </nav>
</template>
<script>
export default {
  name: 'Navigation',
  data: () => ({
    isOnTop: true
  }),

  mounted () {
    document.addEventListener('scroll', this.handleScroll)
  },

  methods:{
    handleScroll(){
      if(window.pageYOffset > 0 ){
        if(this.isOnTop) this.isOnTop = false
      }
      else this.isOnTop = true
    }
  }
}
</script>
<style>

.navbar{
  width: 100%;
  -webkit-transition: all 0.2s linear;
  -moz-transition: all 0.2s linear;
  -o-transition: all 0.2s linear;
  transition: all 0.2s linear;
}

.navbar-brand{
  margin-left: 12.5%;
}
.navbar-nav{
  margin-right: 12.5%;
  text-align: center;
}
.scroll{
  background-color: #484d52;
}
.nav-link{
  font-size: 14px;
  font-family: Montserrat-Bold, sans-serif;
  color: #fdfdff !important;
  margin-right: 2rem;
}

.active{
  color: #ffdc08 !important;
}

@media (max-width: 991px){
  .navbar{
    padding: 0;
    background-color: rgba(22, 27, 32, 0.99) !important;
  }
  .navbar-brand{
    margin-left: 2rem;
    margin-top: 1rem;
    margin-bottom: 1rem;
  }
  .navbar-toggler{
    margin-right: 2rem;
    margin-top: 1rem;
    margin-bottom: 1rem;
  }
  .navbar-nav{
    margin-right: 0;
    padding-top: 2rem;

  }
  .nav-link{
    margin-right: 0;
    font-size: 3vw;
  }

  .navbar-nav{
    height: 92vh;
  }
  .navbar-toggler
  {
    color: #fdfdff !important;
    border: 1px #fdfdff solid !important;
    padding: 0.5rem 1rem;
    font-weight: bold;
    font-size: 3vw;
  }

  .navbar-toggler.collapsed::before{
    content: 'MENU'
  }

  .navbar-toggler.collapsed::after{
    content: ''
  }

  .navbar-toggler::before{
    content: url(../assets/icons/menu.png);
  }
  .navbar-toggler::after{
    content: ' CLOSE';
  }
  .show{
    height: 100vh;
  }
}

@media (max-width: 600px) {
  .navbar{
    padding: 0;
    background-color: rgba(22, 27, 32, 0.99) !important;
  }
  .navbar-brand{
    margin-left: 2rem;
    margin-top: 1rem;
    margin-bottom: 1rem;
  }
  .navbar-toggler{
    margin-right: 2rem;
    margin-top: 1rem;
    margin-bottom: 1rem;
  }
  .navbar-nav{
    margin-right: 0;
    padding-top: 2rem;

  }
  .nav-link{
    margin-right: 0;
  }

  .navbar-nav{
    height: 92vh;
  }
  .navbar-toggler
  {
    color: #fdfdff !important;
    border: 1px #fdfdff solid !important;
    padding: 0.5rem 1rem;
    font-weight: bold;
    font-size: 4vw;
  }

  .navbar-toggler.collapsed::before{
    content: 'MENU'
  }

  .navbar-toggler.collapsed::after{
    content: ''
  }

  .navbar-toggler::before{
    content: url(../assets/icons/menu.png);
  }
  .navbar-toggler::after{
    content: ' CLOSE';
  }
  .show{
    height: 100vh;
  }
}
</style>