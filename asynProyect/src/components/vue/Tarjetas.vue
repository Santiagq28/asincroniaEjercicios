<script setup>
    import {ref} from 'vue';
/*
    async function getData(){
        const data = await fetch('https://thesimpsonsquoteapi.glitch.me/quotes?count=num');
        const dataJSON = await data.json();
        console.log(dataJSON);
        console.log(dataJSON[0].quote);
        getData();
    }*/

    const data2 = ref(await fetch('https://thesimpsonsquoteapi.glitch.me/quotes?count=num').then(res => res.json()));
    console.log(data2);
    const left = "Left";
    const right = "Right";
    
    /* Abajo a la hora de acceder alguna propiedad de los objetos, puedes usar tanto .propiedad o ['propiedad'],
    lo segundo te sirve si el nombre de la propiedad lo proporciona alguna variable*/ 
</script>

<template>
    <div class="flex bg-slate-400 w-[60vh] h-36 p-4 m-4 border border-black justify-around rounded"> 
        <div 
            :class="{'hidden': data2[0].characterDirection  === right}"
            class="w-28 h-28 bg-top bg-cover rounded-full bg-white"
            :style="{backgroundImage:`url(${data2[0]['image']})`}" 
        > 
        </div>
        <div class="grid max-w-[50%]">
            <h2 class="font-bold">{{ data2[0].character }}</h2>
            <p class="text-xs">{{ data2[0].quote }}</p>
        </div>
        <div 
            :class="{'hidden': data2[0].characterDirection  === left}"
            class="w-28 h-28 bg-top bg-cover rounded-full bg-white"
            :style="{backgroundImage:`url(${data2[0].image})`}"
        > 
        </div>
    </div>
</template>