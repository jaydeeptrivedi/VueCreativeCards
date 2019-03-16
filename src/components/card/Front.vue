<template>
    <div class="row">
        <div class="card col-sm-6 edit-area">
            <cc-text-input v-on:displayTextChanged="textBoxValue1=$event"></cc-text-input>
            <cc-text-input v-on:displayTextChanged="textBoxValue2=$event"></cc-text-input>
            <cc-text-input v-on:displayTextChanged="textBoxValue3=$event"></cc-text-input>
        </div>
        <div class="card col-sm-6 card-display">
            <cc-text-output v-bind:displayText="textBoxValue1" v-bind:containerHeight="130"></cc-text-output>
            <cc-text-output v-bind:displayText="textBoxValue2" v-bind:containerHeight="130"></cc-text-output>
            <cc-text-output v-bind:displayText="textBoxValue3" v-bind:containerHeight="130"></cc-text-output>
        </div>
    </div>
</template>

<script>
import TextInput from './TextInput.vue'
import TextOutput from './TextOutput.vue'

export default {
    components:{
        ccTextInput:TextInput,
        ccTextOutput:TextOutput
    },
    data: function(){
        return{
            textBoxValue1:"",
            textBoxValue2:"",
            textBoxValue3:""
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