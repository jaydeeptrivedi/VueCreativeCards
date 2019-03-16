<template>
  <div class="container">
    <div class="row">
      <div class="col-sm-12">
        <nav-header v-on:pageWasChanged="currentPage=$event"></nav-header>
        <component v-bind:is="currentPage"></component>
      </div>
    </div>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import CardFront from './components/card/Front.vue'
import CardBack from './components/card/Back.vue'
import InsideLeft from './components/card/InsideLeft.vue'
import InsideRight from './components/card/InsideRight.vue'

export default{
  components:{
    navHeader: Header,
    cardFront: CardFront,
    cardBack: CardBack,
    insideLeft: InsideLeft,
    insideRight: InsideRight
  },
  data: function(){
    return{
      currentPage: 'cardFront'
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
