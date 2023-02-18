<template>
        <div class="m-auto">
            <h1 class="text-center text-2xl font-bold">DC Heros {{ herosCount }}</h1>
            <ul>
                <li v-for="(hero,index) in dcheros" :key="hero.name" class="flex justify-between">
                    <div>{{ index }}: {{ hero.name }}  </div>
                    <button @click="removeHero(index)">x</button>
                </li>
            </ul>
            <form class="mt-10" @submit.prevent="addHero">
                <input class="border rounded" v-model="newHero" placeholder="Type Super Hero Name">
                <button class="border rounded bg-gradient-to-t from-red-600 to pink-500 text-white" type="submit">Add Hero</button>
            </form> 
        </div>
</template>
<script>
export default {
    data(){
        return{
            newHero:"",
            dcheros:[
                {name:"super girl"},
               { name:"flash"},
                {name:"batman"},
               { name:"ironman"},
               { name:"steelman"}
        ],
        };
    },
    methods:{
        addHero(){
            if (this.mewHero !== " ") {
                this.dcheros.push({name:this.newHero});
            this.newHero=''; 
            }
        },
        removeHero(index){
           this.dcheros=this.dcheros.filter((hero,i) => i != index);
        //    console.log(this.dcheros.filter((hero,i) => i != index));
        }
    },
    computed:{
        herosCount(){
            return this.dcheros.length+' heros';
        },

    }
}
</script>