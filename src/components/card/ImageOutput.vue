<template>
    <div class="imageContainer" v-bind:style="styleObject" v-on:mouseover="showOptions=true" v-on:mouseleave="showOptions=false">

        <transition name="scale">
                <button type="button" class="btn btn-outline-danger btn-sm" v-show="showOptions" v-on:click="clearImageProp">Remove Image</button>
        </transition>
          
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
        },
        clearImageProp: Function
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
            if(this.displayImage=="") 
            {
                document.getElementById('outputImage').src="";
            }
            else
            {

                var storageRef = Firebase.storage().ref('user_uploads/'+this.displayImage);
                storageRef.getDownloadURL().then(function(url){
                    var img = document.getElementById('outputImage');
                    img.src=url;
                    setDraggable();
                })
            }
        }
    }
    
}

function setDraggable(){
    $('#outputImage').draggable();
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

img{
    width:130%
}

.scale-enter-active{
    animation: scale-in 0.5s;
}

.scale-leave-active{
    animation: scale-out 0.5s;
}

</style>
