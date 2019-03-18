<template>
    <div class="row">
        <div class="col-sm-12">
            <h4>Upload Image</h4>
            <div class="form-group">
                <input class="form-control-file" id="fileUpload" type="file" v-on:change="uploadFile">
            </div>
            <br>
            <progress value="0" max="100" id="progressBar"></progress>
            <img id="image"  alt="image">
            <button type="" style="display:none" id="setImageButton" v-on:click="setImage">Set Image</button>
        </div>
    </div>
</template>

<script>
import Firebase from 'firebase'
export default {
    data: function(){
        return{
            file:'',
            imgSource:''
        }
    },
    methods:{
        uploadFile: function(event){
            document.getElementById('setImageButton').style.display='none';

            this.file=event.target.files[0];
            var storageRef = Firebase.storage().ref('user_uploads/'+this.file.name);
            var upload = storageRef.put(this.file);

            var reader = new FileReader();
            reader.readAsDataURL(this.file);

            reader.onload = function(e){
                document.getElementById('image').src = e.target.result
            }

            upload.on('state_changed', function(snapshot){
                var progress = (snapshot.bytesTransferred/snapshot.totalBytes)*100;
                document.getElementById('progressBar').value = progress;
                if(progress==100)
                    document.getElementById('setImageButton').style.display='inline-block';
            })
        },
        setImage: function(){
            this.$emit('displayImageChanged',this.file.name)
        }
    }
}
</script>

<style scoped>
img{
    max-height: 200px
}
</style>

