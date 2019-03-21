<template>
    <div class="row">
        <div class="card col-sm-6 edit-area">
            <cc-image-upload v-on:displayImageChanged="imageName=$event"></cc-image-upload><hr>
            <cc-section-completed></cc-section-completed>
        </div>
        <div class="card col-sm-6 card-display">
            <cc-image-output v-bind:displayImage="imageName" v-bind:containerHeight="350" v-bind:clearImageProp="clearImage"></cc-image-output>
        </div>
    </div>
</template>

<script>
import ImageUpload from './ImageUpload.vue'
import ImageOutput from './ImageOutput.vue'
import SectionCompleted from './SectionCompleted.vue'

export default {
    components:{
        ccImageUpload:ImageUpload,
        ccImageOutput:ImageOutput,
        ccSectionCompleted:SectionCompleted
    },
    data: function(){
        return{
            imageName:""
        }
    },
    methods:{
        clearImage: function(){
            this.imageName='';
        }
    }
}
</script>

