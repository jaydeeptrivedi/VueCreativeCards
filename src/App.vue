<template>
  <div class="container">
    <div class="row">
      <div class="col-sm-12">
        <nav-header v-on:pageWasChanged="currentPage=$event"></nav-header>
        <div id="instructions" class="text-center italic">
          <div class="row">
              <div class="col-sm-6">
                <p><em>&larr; Make changes in the edit card area below</em></p>
              </div>
               <div class="col-sm-6">
                <p><em>And they will show on the card &rarr;</em></p>
              </div>
          </div>
        </div>
        <transition name="fade" mode="out-in" v-on:enter="enter">
          <keep-alive>
            <component v-bind:is="currentPage"></component>
          </keep-alive>
        </transition>
        <cc-footer>
          <p class="text-center">&copy; {{appName}}</p>
          <nav>
            <ul class="nav justify-content-center">
              <li class="nav-item"><a class="nav-link">Home</a></li>
              <li class="nav-item"><a class="nav-link">About Us</a></li>
              <li class="nav-item"><a class="nav-link">Contact Us</a></li>
            </ul>
          </nav>
        </cc-footer>
      </div>
    </div>
  </div>
</template>

<script>
import FirebaseConfig from './firebaseConfig.js'
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'
import CardFront from './components/card/Front.vue'
import CardBack from './components/card/Back.vue'
import InsideLeft from './components/card/InsideLeft.vue'
import InsideRight from './components/card/InsideRight.vue'

export default{
  components:{
    navHeader: Header,
    ccFooter: Footer,
    cardFront: CardFront,
    cardBack: CardBack,
    insideLeft: InsideLeft,
    insideRight: InsideRight
  },
  data: function(){
    return{
      currentPage: 'cardFront',
      appName: 'Creative Cards'
    }
  },
  methods:{
    enter: function(el){
      document.getElementById("instructions").style.display="none";
    }
  }
}
</script>

<style>
body{
  font-family: Verdana, Geneva, Tahoma, sans-serif;
  color: #333;
}

a{
  cursor: pointer;
}

.fade-enter, .fade-leave-to{
    opacity: 0;
}

.fade-enter-active{
    transition: 0.5s;
}

.fade-leave-active{
    transition: 0.5s;
}

@keyframes scale-in {
    0% {transform: scale(0);}
    100% {transform: scale(1);}
}

@keyframes scale-out {
    0% {transform: scale(1);}
    100% {transform: scale(0);}
}
</style>
