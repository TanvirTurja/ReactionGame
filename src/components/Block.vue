<template>
    <div class="w-full max-w-sm px-4 py-3 mx-auto " v-if="showBlock" @click="stopTimer">
        
        <div >
            <h1 class="bg-indigo-800 text-white font-bold rounded-lg border shadow-lg p-10" >CLICK ME</h1>
        </div>

        
    </div>
</template>

<script>
    export default {
        name:'Block',
        props: ['delay'],
        data(){
            return{
                showBlock: false,
                timer: null,
                reactionTime: 0
            }
        },
        mounted(){
            setTimeout(() => {
                this.showBlock = true
                this.startTimer()
            }, this.delay)
          
        },
        methods:{
            startTimer(){
                this.timer = setInterval(() => {
                    this.reactionTime += 10
                }, 10)
            },
            stopTimer(){
                clearInterval(this.timer)
                console.log(this.reactionTime);
                this.$emit('end', this.reactionTime)
            }
        }
       
    }
</script>

<style scoped>

</style>