<template>

    <div class="card">
        <h3 v-text="'Game ' + id"></h3>
        <div v-show="!edit">
            <h4 @click="setWinner(1)" :class="['team',{loser:isLoser(1)}]">{{team1name | uppercase}}</h4>
            <h4 @click="setWinner(2)" :class="['team',{loser:isLoser(2)}]">{{team2name | uppercase}}</h4>
            <button @click.prevent="edit = !edit">Edit</button>
        </div>
        <div v-show="edit">
            <div>Team 1:
                <input type="text" v-model="team1">
            </div>
            <div>Team 2:
                <input type="text" v-model="team2">
            </div>
            <button @click.prevent="edit = !edit">Submit</button>
        </div>
    </div>

</template>

<script>
export default{
    name:"",
    props:{
        'id':Number,
        'next':Number,
        pos:Number,
        't1':{
            type:String,
            default:""
        },
        't2':{
            type:String,
            default:""
        },
    },
    components:{},
    mounted(){
        this.setWinner = function(num){
            this.winner = num;
            this.$root.$emit('win',this.next,this.pos,this['team'+num+'name']);
        }
    },

    mixins:[],
    data(){
        return {
            edit:false,
            team1:"",
            team2:"",
            winner:0,
        }
    },
    methods:{
        isLoser(num){
            if(this.winner != 0){
                return this.winner != num;
            }
            return false;
        },
    },
    computed:{
        team1name(){
            return this.t1 || this.team1;
        },
        team2name(){
            return this.t2 || this.team2;
        }
    },
    filters:{
        uppercase(value){
            return value.toUpperCase();
        }
    },

}
</script>

<style scoped>
.card{
    margin-bottom:5%;
}
.team{
    text-decoration:underline;
}
.team.loser{
    text-decoration:line-through;
}
</style>

