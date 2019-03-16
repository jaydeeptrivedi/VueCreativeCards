<template>
  <div class="container">
    <div class="row">
      <div class="col-sm-12">
        <nav-header v-on:pageWasChanged="currentPage=$event"></nav-header>
        <keep-alive>
          <component v-bind:is="currentPage"></component>
        </keep-alive>
        <footer>
          <p class="text-center">&copy; {{appName}}</p>
          <nav>
            <ul class="nav justify-content-center">
              <li class="nav-item"><a class="nav-link">Home</a></li>
              <li class="nav-item"><a class="nav-link">About Us</a></li>
              <li class="nav-item"><a class="nav-link">Contact Us</a></li>
            </ul>
          </nav>
        </footer>
      </div>
    </div>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'
import CardFront from './components/card/Front.vue'
import CardBack from './components/card/Back.vue'
import InsideLeft from './components/card/InsideLeft.vue'
import InsideRight from './components/card/InsideRight.vue'

export default{
  components:{
    navHeader: Header,
    footer: Footer,
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
</style>
