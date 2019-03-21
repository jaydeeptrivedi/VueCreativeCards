<template>
    <div class="row">
        <div class="card col-sm-6 edit-area">
            <cc-text-input v-on:displayTextChanged="textBoxValue1=$event"></cc-text-input>
        </div>
        <div class="card col-sm-6 card-display">
            <cc-text-output v-bind:displayText="textBoxValue1" v-bind:containerHeight="750"></cc-text-output>
        </div>
    </div>
</template>

<script>

import TextInput from './TextInput.vue'
import TextOutput from './TextOutput.vue'

export default {
    data: function(){
        return{
            textBoxValue1:''
        }
    },
    components:{
        ccTextInput:TextInput,
        ccTextOutput:TextOutput
    }
}
</script>

<style>

</style>