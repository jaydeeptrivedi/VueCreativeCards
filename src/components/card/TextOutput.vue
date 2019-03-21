<<template>
    <div v-on:mouseover="showOptions=true" v-on:mouseleave="showOptions=false">
        <form class="small" v-show="showOptions">
            <label for="selectBox">Font size:</label>
            <select class="small" id="selectBox" v-model="setFontSize">
                <option value="42">42px</option>
                <option value="48">48px</option>
                <option value="52">52px</option>
                <option value="64">64px</option>
            </select>
            <div class="form-check form-check-inline">
                <label class="form-check-label">
                    <input type="radio" class="form-check-input" value="left" v-model="setTextAlign">Left
                </label>
            </div>
            <div class="form-check form-check-inline">
                <label class="form-check-label">
                    <input type="radio" class="form-check-input" value="center" v-model="setTextAlign">Center
                </label>
            </div>
            <div class="form-check form-check-inline">
                <label class="form-check-label">
                    <input type="radio" class="form-check-input" value="right" v-model="setTextAlign">Right
                </label>
            </div>
            <div class="form-check form-check-inline">
                <label class="form-check-label">
                    <input type="checkbox" class="form-check-input" value="right" v-model="setBold">Bold
                </label>
            </div>
            <div class="form-check form-check-inline">
                <label class="form-check-label">
                    <input type="checkbox" class="form-check-input" value="right" v-model="setItalic">Italic
                </label>
            </div>
        </form>
        <p v-bind:style="styleObject" :class="{bold:setBold, italic:setItalic}">{{displayText}}</p>     
    </div> 
</template>

<script>
export default {
    props:{
        displayText: [String],
        containerHeight: {
            type: Number,
            default: 200
        }
    },
    data: function(){
        return{
            showOptions:false,
            setFontSize:'42',
            setTextAlign:'',
            setBold:false,
            setItalic:false
        }
    },
    computed: {
        styleObject: function(){
            return {
                height: this.containerHeight + 'px',
                fontSize: this.setFontSize + 'px',
                textAlign: this.setTextAlign
            }
        }
    },
}
</script>

<style scoped>
p {
    font-family: 'Tangerine', cursive;
    font-size: 42px;
    line-height: 110px;
    color: #4d4d4d;
    text-shadow: 2px 2px 2px #aaa;
    margin: 5px 0;
    border: 1px dotted grey;
    white-space: pre-line;
    overflow: hidden;
}

.bold{
    font-weight: bold;
}

.italic{
    font-style: italic;
}

form{
    position: absolute;
    border-bottom: 1px dotted gray;
    margin-top: 10px;
    margin-bottom: 5px;
    padding-bottom: 5px;
}

select{
    height: 40%;
}
</style>