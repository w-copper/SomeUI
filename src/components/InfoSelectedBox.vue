<template>
    <div id="container" @click="click" :style="{width:width+'px'}">
        <div id="avater" :style="{width:width-10+'px', height:height-10+'px'}">
            <!-- img -->
            <div id="checked" v-show="checked" :style="{paddingTop:paddingTop+'px',width:width-10+'px', height:height+'px' }">
                <i >
                    <svg t="1568118862648" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="2324" :width="sSize" :height="sSize"><path d="M512.024381 0C229.205333 0 0 229.205333 0 512.024381 0 794.770286 229.205333 1024 512.024381 1024 794.770286 1024 1024 794.770286 1024 512.024381 1024 229.205333 794.770286 0 512.024381 0M849.603048 353.328762l-385.462857 385.462857c-9.411048 9.411048-21.723429 14.09219-34.06019 14.09219s-24.697905-4.681143-34.084571-14.09219l-221.622857-221.647238c-18.822095-18.822095-18.822095-49.322667 0-68.120381 18.822095-18.846476 49.322667-18.846476 68.144762 0l187.562667 187.562667 351.378286-351.402667c18.822095-18.822095 49.322667-18.822095 68.144762 0C868.425143 304.006095 868.425143 334.506667 849.603048 353.328762" fill="#1afa29" p-id="2325"></path></svg>
                </i>
            </div>
            <div >
                <slot name="avater"></slot>
            </div>
        </div>
        <div id="description">
            <!-- description -->
            <slot>描述</slot>
        </div>
    </div>
</template>

<script>

export default {
    name : 'InfoSelectedBox',
    props : {
        call : Function,
        checked : Boolean,
        width : {
            required : false,
            type : Number,
            default : 100,
        },
        height : {
            required : false,
            type : Number,
            default : 100,
        }
    },
    data(){
        return {

        }
    },
    computed: {
        sSize(){
            return  this.width > this.height ? this.height / 2 : this.width / 2;
        },
        paddingTop(){
            return this.height/2 - 5 - this.sSize/2;
        }
    },

    methods: {
        click(){
            this.changeStyle();
            if(this.call)
            {
                this.call();
            }
        },
        changeStyle(){
        }
    },
}
</script>

<style scoped>
#container{
    position: relative;
    background: rgb(198, 237, 255);
    border-radius: 10%;
    box-shadow: 5px 5px 5px rgba(67, 67, 67, 0.616);
    float: left;
    padding: 3px;
    margin: 5px;
}

#container:hover{
    cursor: pointer;
}

#checked{
    position: absolute;
    /* padding: 20px; */
    /* background: #0000002b; */
}

#description{
    height: fit-content;
    min-height: fit-content;
    border-top: solid 2px #0d0d0d2e;
    padding: 5px;
}

#avater{
    background: #38edf647;
    border-radius: 50%;
    border : solid 5px #00000000;
    transition: all .5s;
    overflow: hidden;
}

#avater:hover {
    border-radius: 10%;
}
</style>
