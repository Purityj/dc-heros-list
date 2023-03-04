<template>
    <div class="m-auto">
        <h2 class="text-center text-2xl">DC Heros List [{{ heroCount }}]</h2>
        <ul>
          <li class="flex justify-between" v-for="(hero, index) in dcHero" :key="hero.name" >  
              <div>
                  {{ hero.name }}   
              </div> 
              <button @click="removeHero(index)">x</button>
          </li>
        </ul>
        <form class="mt-10" @submit.prevent="addHero">
          <input class="border rounded mr-2" placeholder="Type hero name" v-model="newHero">
          <button class="border rounded bg-gradient-to-r from-red-700 to-pink-500 text-white" type="submit">Add hero</button>
        </form>
        <small>Total heros: {{ heroCount }}</small>
       </div>
</template>

<script>
export default {
    computed: {
        heroCount() {
            return this.dcHero.length;
        }
    },

    methods: {
        addHero() {
           if(this.newHero !== ""){
             this.dcHero.push({name: this.newHero});
             this.newHero = "";
           }
        },
        // remove hero
        removeHero(index){
            this.dcHero = this.dcHero.filter((hero, i) => i !== index);
        },
    
},
    data() {
        return {
            dcHero: [
                {name: "Superman"},
                {name: "Batman"},
                {name: "Supergirl"},
                {name: "Flash"},
                {name: "Arrow"},
            ],
            newHero: "",
        };

    },
}

</script>

<style> 

</style>