<template>
    <div class="container-fluid">
        <div class="row">
            <div @win="onWin" class="col-xs-12 col-md-4">
                <h1>Round 1</h1>
                <game :id=1 :pos=1 :next=5></game>
                <game :id=2 :pos=2 :next=5></game>
                <game :id=3 :pos=1 :next=6></game>
                <game :id=4 :pos=2 :next=6></game>

            </div>
            <div class="col-xs-12 col-md-4">
                <h1>Round 2 </h1>
                <game :id=5 :next=7 :pos=1 :t1="g5t1" :t2="g5t2"></game>
                <game :id=6 :next=7 :pos=2 :t1="g6t1" :t2="g6t2">></game>

            </div>
            <div class="col-xs-12 col-md-4">
                <h1>Round 3</h1>
                <game :id=7 :t1="g7t1" :t2="g7t2"></game>
            </div>
        </div>
    </div>

</template>

<script>
import game from '@/components/game'

export default{
    name:"bracket",
    props:[],
    components:{game},
    mixins:[],
    mounted(){
        this.$root.$on('win',this.onWin)
    },
    data(){
        return {
            g5t1:"",
            g5t2:"",
            g6t1:"",
            g6t2:"",
            g7t1:"",
            g7t2:"",
        }
    },
    methods:{
        onWin(gameId,teamPos,teamName){
            console.log(gameId,teamPos,teamName);
            this['g'+gameId+'t'+teamPos] = teamName;
        }
    },
    computed:{},
}
</script>

<style scoped>
</style>

