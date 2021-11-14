<template>
    <div class="block" v-if="showBlock" @click="stopTimer">
        Click me
    </div>
</template>
<script>
export default {
    props:['delay',],
    data(){
        return{
            showBlock: false,
            timer: null,
            reactionTime: 0,
        }
    },
    mounted(){
        setTimeout(()=>{
            this.showBlock = true
            this.starttimer()
        }, this.delay)
    },
    methods:{
        starttimer(){
            this.timer = setInterval(() => {
                this.reactionTime += 10
            }, 10);
        },
        stopTimer(){
            clearInterval(this.timer)
            this.$emit('end', this.reactionTime)
        }
    }
    /*
    updated(){
        console.log('component updated')
    },
    unmounted(){
        console.log('component unmounted')
    }
    */
}
</script>
<style>
.block {
    width: 400px;
    border-radius: 20px;
    background: #0faf87;
    color: white;
    text-align: center;
    padding: 100px 0;
    margin: 40px auto;
    }
</style>