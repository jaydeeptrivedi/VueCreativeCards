<template>
<div>
    <h1 class="text-center">Creative Cards</h1>
    <ul class="nav justify-content-center">
        <li class="nav-item"><a class="nav-link" v-on:click="pageSelected='cardFront'">Front</a></li>
        <li class="nav-item"><a class="nav-link" v-on:click="pageSelected='insideLeft'">Inside Left</a></li>
        <li class="nav-item"><a class="nav-link" v-on:click="pageSelected='insideRight'">Inside Right</a></li>
        <li class="nav-item"><a class="nav-link" v-on:click="pageSelected='cardBack'">Back</a></li>
    </ul>
    <hr>
    <cc-card-progress></cc-card-progress>
</div>  
</template>

<script>
import CardProgress from './card/CardProgress.vue'

export default {
    components:{
        ccCardProgress:CardProgress
    },
    data: function(){
        return {
            pageSelected:''
        }
    },
    watch: {
        pageSelected: function () {
            this.$emit('pageWasChanged', this.pageSelected)
        }
    }
}
</script>

<style>
h1 {
    margin-top: 10px
}
</style>
