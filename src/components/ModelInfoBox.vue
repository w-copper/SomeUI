<template>
    <div class="container" 
    :style="{ width : cWidth + 'px', height : cHeight + 'px', padding : '5px' }" 
    @mouseover="mouseOver"
    @mouseleave="mouseLeave">
        <div class="avater" :style="{width : width +'px', height : height + 'px'}">
            <div >
                <slot></slot>
            </div>
        </div>
        <div class="menu" :style="{width : menuWidth + 'px', height : cHeight + 15 + 'px', left : menuLeft + 'px' }">
            <div class="info" @click="info_" >
                <i>
                    <svg t="1568204993013" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="2008" width="16px" height="16px"><path d="M576 736l-32 0 0-286.016c0-0.352-0.096-0.672-0.096-0.992s0.096-0.64 0.096-0.992c0-17.664-14.336-32-32-32l-64 0c-17.664 0-32 14.336-32 32s14.336 32 32 32l32 0 0 256-32 0c-17.664 0-32 14.336-32 32s14.336 32 32 32l128 0c17.664 0 32-14.336 32-32s-14.336-32-32-32zM512 352c35.36 0 64-28.672 64-64s-28.64-64-64-64-64 28.672-64 64 28.672 64 64 64zM512 0c-282.752 0-512 229.216-512 512s229.216 512 512 512c282.784 0 512-229.216 512-512s-229.216-512-512-512zM512 960.992c-247.04 0-448-201.984-448-449.024s200.96-448 448-448 448 200.96 448 448-200.96 449.024-448 449.024z" p-id="2009" fill="currentColor"></path></svg>
                </i>
            </div>
            <div class="pos" @click="pos_" >
                <i>
                    <svg t="1568205060882" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="2800" width="24px" height="24px"><path d="M512 1014.857A502.857 502.857 0 1 1 1014.857 512 503.406 503.406 0 0 1 512 1014.857z m0-969.143A466.286 466.286 0 1 0 978.286 512 466.834 466.834 0 0 0 512 45.714z" fill="currentColor" p-id="2801"></path><path d="M725.577 281.417C705.646 291.474 208.64 531.566 208.64 531.566s168.411 101.668 166.766 100.023l100.023 182.857s263.497-508.16 266.788-516.389c3.292-11.703-4.937-21.76-16.64-16.64zM275.383 531.383l382.903-183.954-266.24 250.697zM475.429 748.25S423.68 648.23 408.686 614.766l266.788-256z m0 0" fill="currentColor" p-id="2802"></path></svg>
                </i>
            </div>
            <div class="del" @click="del_" >
                <i>
                    <svg t="1568205152174" class="icon" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg" p-id="3618" width="16px" height="16px"><path d="M731.918 180.534H293.285c-40.383 0-73.106 32.72-73.106 73.103v24.368h584.844v-24.368c0.001-40.383-32.72-73.103-73.105-73.103m-127.696-48.735l10.756 76.91H410.225l10.756-76.91h183.24m5.855-48.735H415.128c-20.108 0-38.813 16.277-41.621 36.218L359.252 221.25c-2.784 19.917 11.4 36.194 31.508 36.194h243.685c20.108 0 34.293-16.276 31.484-36.217l-14.255-101.969c-2.786-19.917-21.49-36.194-41.598-36.194m134.026 243.675H281.1c-26.795 0-46.761 21.845-44.334 48.544l39.933 438.996c2.403 26.7 26.344 48.544 53.14 48.544h365.527c26.795 0 50.736-21.845 53.14-48.544l39.932-438.996c2.426-26.699-17.54-48.544-44.336-48.544M415.128 765.353h-73.106L317.653 424.21h97.474v341.144z m146.211 0h-97.474V424.21h97.474v341.144z m121.842 0h-73.106V424.21h97.474l-24.368 341.144z" fill="currentColor" p-id="3619"></path></svg>
                </i>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name : 'ModelInfoBox',
    data(){
        return {
            menuWidth : 30,
            menuLeft : -31,
        }
    },
    props : {
        width : {
            type : Number,
            required : false,
            default : 200,
        },
        height : {
            type : Number,
            required : false,
            default : 100,
        },
        info : Function,
        pos : Function,
        del : Function,
    },
    computed: {
        cWidth(){
            return this.width + 5 + 5 ;
        },
        cHeight(){
            return this.height + 5 + 5;
        }
    },
    methods: {
        mouseOver(){
            this.menuLeft = 0;
        },
        mouseLeave(){
            this.menuLeft = -this.menuWidth-1;
        },
        info_(){
            if(this.info){
                this.info();
            }
        },
        pos_(){
            if(this.pos){
                this.pos();
            }
        },
        del_(){
            if(this.del){
                this.del();
            }
        }
    },
}
</script>

<style scoped>
.container{
    position: relative;
    background: rgba(41, 41, 41, 0.198);
    border-radius: 10%;
    vertical-align: middle;
    text-align: center;
    color : white;
    overflow: hidden;
    margin: 5px;
    box-shadow: 5px 5px 5px #7a7a7a;
}
.avater{
    float: left;
    overflow: hidden;
    border: solid 5px #00000000;
    border-radius: 10%;
    width: 140px;
    height: 90px;
    transition: all 0.5s;
}
.avater:hover{
    border-radius: 5%;
}
.menu{
    position: absolute;
    margin: 0;
    top:-5px;
    /* border-left: solid 1px white; */
    transition: all 0.5s;
    background: #0000004f;
    cursor: pointer;
}

.info{
    padding-top : calc(30% + 5px);
    color : rgba(255, 255, 255, 0.7);
    transition: color 0.5s;
}

.info:hover{
    color :rgb(255, 255, 255);
}

.pos{
    padding-top : calc(30% + 5px);
    padding-bottom: calc(30%);
    border-top : solid 1px;
    border-bottom: solid 1px;
    color: rgba(116, 243, 243, 0.7);
    transition: color 0.5s;
}

.pos:hover{
    color: aqua;
}

.del{
    padding-top : 5px;
    color: aliceblue;
    transition: color 0.5s;
}
.del:hover{
    color: red;
}

</style>
