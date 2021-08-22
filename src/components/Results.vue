<template>
    <div>
           <p class="text-lg text-center" >Reaction time : {{score}} ms</p>
           <p class="text-lg text-center">{{rank}}</p>
    </div>
</template>

<script>
    export default {
        name:'Results',
        props:['score'],
        data(){
            return{
            rank: null
            }
        },
        mounted(){
            if(this.score <240)
            {
                this.rank = 'Ninja finger'
            }
            else if (this.score < 350)
            {this.rank = 'Rapid Reflex'}
            else{
                this.rank = 'Snail pace'
            }
        }
    }
</script>

<style scoped>

</style>