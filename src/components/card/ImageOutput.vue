<template>
    <div class="imageContainer" v-bind:style="styleObject" v-on:mouseover="showOptions=true" v-on:mouseleave="showOptions=false">

        <button type="button" class="btn btn-outline-danger btn-sm" v-show="showOptions">Remove Image</button>  
        <img id='outputImage'>{{displayImage}}
    </div>
</template>

<script>
import Firebase from 'firebase'

export default {
    props:{
        displayImage:{
            type: String
        },
        containerHeight: {
            type: Number,
            default: 200
        }
    },
    data: function(){
        return {
            showOptions: false
        }
    },
    computed: {
        styleObject: function(){
            return {
                height: this.containerHeight + 'px'
            }
        }
    },
    watch:{
        displayImage: function(){
            var storageRef = Firebase.storage().ref('user_uploads/'+this.displayImage);
            storageRef.getDownloadURL().then(function(url){
                var img = document.getElementById('outputImage');
                img.src=url
            })
        }
    }
    
}
</script>

<style scoped>
.imageContainer{
    border: 1px dotted;
    overflow: hidden;
    margin: 5px 0;
}

button{
    position: absolute;
    z-index: 1;
}
</style>
