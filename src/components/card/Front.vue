<template>
    <div class="row">
        <div class="card col-sm-6 edit-area">
            <cc-text-input v-on:displayTextChanged="textBoxValue1=$event"></cc-text-input>
            <cc-image-upload v-on:displayImageChanged="imageName=$event"></cc-image-upload><hr>
            <cc-text-input v-on:displayTextChanged="textBoxValue2=$event"></cc-text-input>
            <cc-text-input v-on:displayTextChanged="textBoxValue3=$event"></cc-text-input>
            <cc-section-completed></cc-section-completed>
        </div>
        <div class="card col-sm-6 card-display">
            <cc-text-output v-bind:displayText="textBoxValue1" v-bind:containerHeight="130"></cc-text-output>
            <cc-image-output v-bind:displayImage="imageName" v-bind:containerHeight="350" v-bind:clearImageProp="clearImage"></cc-image-output>
            <cc-text-output v-bind:displayText="textBoxValue2" v-bind:containerHeight="130"></cc-text-output>
            <cc-text-output v-bind:displayText="textBoxValue3" v-bind:containerHeight="130"></cc-text-output>
        </div>
    </div>
</template>

<script>
import TextInput from './TextInput.vue'
import TextOutput from './TextOutput.vue'
import ImageUpload from './ImageUpload.vue'
import ImageOutput from './ImageOutput.vue'
import SectionCompleted from './SectionCompleted.vue'

export default {
    components:{
        ccTextInput:TextInput,
        ccTextOutput:TextOutput,
        ccImageUpload:ImageUpload,
        ccImageOutput:ImageOutput,
        ccSectionCompleted:SectionCompleted
    },
    data: function(){
        return{
            textBoxValue1:"",
            textBoxValue2:"",
            textBoxValue3:"",
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

<style>
.edit-area{
    background-color: #d2f9f9;
    height: 800px;
    padding: 20px;
}
.card-display{
    height: 800px;
    padding: 20px;
}
</style>