<template>
    <div class="block" @click="handleReactionTime(), emitCloseBlock()">
        <h1>click me!</h1>
    </div>
</template>

<script>
export default {
    name: "Block",
    data(){
        return{
            timeAfterMounted: Number,
            timeAfterClick: Number,
            reactionTime: Number
        }
    },
    mounted: function(){
        this.getAfterMountedTime();
    },
    methods: {
        getAfterMountedTime(){
            const oDate = new Date;
            this.timeAfterMounted = oDate.getTime();
        },
        handleReactionTime(){
            const oDate = new Date;
            this.timeAfterClick = oDate.getTime();
            this.reactionTime = this.timeAfterClick - this.timeAfterMounted;
        },
        emitCloseBlock(){
            this.$emit("closeBlock", this.reactionTime)
        }
    }
}
</script>

<style>
    #app div.block {
        background-color: rgb(250, 114, 141);
        color: white;
        height: 250px;
        width: 250px;
        text-transform: uppercase;
        display: flex;
        justify-content: center;
        justify-items: center;
        align-items: center;
    }
</style>