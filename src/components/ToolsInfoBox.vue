<template>
    <div class="container" 
        @click="click" 
        :style="{width:width+'px'}" 
        @mouseover="mouseOver" 
        @mouseleave="mouseLeave">
        <div class="avater" :style="{width:width-20+'px'}">
            <div>
                <w-icon :type="type" :width="sSize" :height="sSize" />
            </div>
        </div>
        <div class="description" :style="{borderTopColor:borderTopColor, color:color}">
            <slot>描述</slot>
        </div>
    </div>
</template>

<script>
import WIcon from './WIcon'

export default {
    name : 'InfoSelectedBox',
    components:{
        WIcon,
    },
    props : {
        call : Function,
        width : {
            required : false,
            type : Number,
            default : 100,
        },
        height : {
            required : false,
            type : Number,
            default : 100,
        },
        type : {
            required: false,
            type:String,
            default:'point'
        }
    },
    data(){
        return {
            borderTopColor : 'black',
            color : 'black',
        }
    },
    
    computed: {
        sSize(){
            return  this.width > this.height ? this.height / 3 * 2- 3: this.width /3 * 2 -3;
        },
    },

    methods: {
        click(){
            if(this.call)
            {
                this.call();
            }
        },
        mouseOver(){
            this.borderTopColor = 'aqua';
            // this.color = '';
        },
        mouseLeave(){
            this.borderTopColor = '#0d0d0d2e';
            this.color = 'black'
        }
    },
    created() {

    },
}
</script>

<style scoped>
.container{
    position: relative;
    background: rgba(223, 224, 224, 0.856);
    /* border-radius: 10%; */
    /* box-shadow: 5px 5px 5px rgba(67, 67, 67, 0.616); */
    float: left;
    padding: 10px;
    margin: 5px;
    margin-right: 10px;
    text-align: center;
    color:rgba(223, 224, 224, 0.856);
}

.container:hover{
    cursor: pointer;
}

.description{
    height: fit-content;
    min-height: fit-content;
    /* border-top: solid 2px #0d0d0d2e; */
    margin-top: 5px;
    padding: 0px;
    font-size: medium;
    transition: all .5s;
}

.avater{
    padding: 10px;
    background: inherit;
    border-radius: 50%;
    border : solid 2px #00000000;
    transition: all .5s;
    overflow: hidden;
    color:rgb(58, 58, 58);
}

.avater:hover {
    border-color: aqua;
    background: teal;
    color:aqua;
}
</style>
