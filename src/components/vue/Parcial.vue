<script setup>
    import {ref} from 'vue';
    import { computed } from 'vue';

    const selecciones = ref([
        [{"name":"cortarse las uñas","icon":"ic--sharp-square.png","color":"bg-blue-600"},
        {"name":"vencer una resistencia con poco esfuerzo","icon": 'mdi--triangle.png',"color":"bg-yellow-600"},
        {"name":"saltar a la comba","icon":"fa6-solid--diamond.png","color":"bg-green-600"},
        {"name":"apretar un tornillo","icon":"ic--baseline-circle.png","color":"bg-red-600"}], // pregunta 1
        [], //pregunta 2
        [], //pregunta 3
        [] //pregunta n
]);


    const count = ref(-1);

    const fondo = ref(0)

    const respuestas = [1,2,3];

    const bar1Class = computed(() => ({
        'bg-green-600': count == respuestas[count],'bg-red-600': fondo.value == respuestas[fondo],
    }));

    function cambiar(i){
        count.value = i;
    }

</script>
<template>
    <div class="h-screen">
        <!-- ufpso -->
        <div class="flex w-full h-1/2 bg-white p-4">
             <div class="bg-blue-600 flex m-auto w-1/2 h-full"> <!-- :class="bar1Class" -->
                <p class="flex m-auto text-white text-5xl text-bold">UFPSO</p>
            </div>
        </div>
        <!-- respuestas -->
        <div class="h-1/2 grid gap-2 grid-cols-2 items-center bg-slate-300">
            <div  class="w-full " v-for="(sel,i) in selecciones[0]" :key="i">
                <!-- iconos -->
                <!-- respuestas -->
                <button class="flex w-11/12 m-2 p-6 text-white" 
                @click="fondo=i,cambiar(i)" :class="sel.color">
              
                    <img :src="sel.icon" class="w-6 mr-2" />
                    {{ sel.name }}
                </button>
            </div>
        </div>
    </div>
</template>