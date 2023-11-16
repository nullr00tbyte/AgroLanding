<template>
    <div @click="navigate('blogs/' + MOCK.slug)"
        class="flex flex-col md:w-2/3 relative md:hover:drop-shadow-[0_35px_35px_rgba(131,166,5,1)]  md:drop-shadow-[0_35px_35px_rgba(4,64,53,1)]">

        <img transition:name="hero" alt="TEST" :src="MOCK.image" loading="lazy"  class="animate-fade-in w-full h-full rounded-tl-[400px]  ">
        <div class="bg-[#044035] md:bg-[#044035B3] hover:bg-[#044035] w-full md:h-1/4 md:absolute md:bottom-0 text-white p-8 ">
            <p class="text-2xl">
                {{ MOCK.title }} - {{ MOCK.author }}

            </p>
            <p class="text-sm text-gray-200">{{ MOCK.date }}</p>
            <p class="text-sm mt-2">
                {{ MOCK.description }}
            </p>

            <div class="mt-5 overflow-auto">
                <span v-for="(tag, idx) in MOCK.tags" v-bind:key="idx"
                    class="bg-blue-100 text-blue-800 text-xs font-medium mr-2 px-2.5 py-0.5 rounded dark:bg-[#F2F2F2] dark:text-black uppercase">{{
                        tag }}</span>
            </div>

        </div>
    </div>
</template>
  
<script setup>
import { ref, onMounted } from 'vue';
import { navigate } from 'astro:transitions/client';
import { Image } from 'astro:assets';

const INITIAL_DATA = [{
    "image": "/1.webp",
    "title": "Innovaciones en la Producción de Maíz",
    "description": "Exploraremos las últimas tecnologías y prácticas en la producción de maíz que están revolucionando la agroindustria. Desde el uso de semillas mejoradas hasta técnicas avanzadas de manejo del suelo, descubre cómo los agricultores están optimizando sus cultivos para obtener cosechas más abundantes y sostenibles.",
    "author": "María González",
    "date": "2023-11-05",
    "tags": ["agroindustria", "maíz", "tecnología agrícola", "sostenibilidad"],
    "slug": "innovaciones-en-la-produccion-de-maiz"
},
{
    "image": "2.webp",
    "title": "Cultivo Sostenible de Cebollas",
    "description": "Descubre las prácticas innovadoras en la plantación de cebollas que promueven la sostenibilidad y la conservación del agua en la agricultura. Exploraremos las técnicas de riego eficientes y cómo la agroindustria está contribuyendo a la preservación del medio ambiente.",
    "author": "Juan Pérez",
    "date": "2023-11-02",
    "tags": ["agroindustria", "cebollas", "sostenibilidad", "riego"],
    "slug": "cultivo-sostenible-de-cebollas"
}];

const ACTUAL_SLIDE = ref(0)

const MOCK = ref(INITIAL_DATA[ACTUAL_SLIDE.value]);


onMounted(() => {
    window.setInterval(() => {
        if (ACTUAL_SLIDE.value + 1 > INITIAL_DATA.length) {
            ACTUAL_SLIDE.value = 0
        }
        MOCK.value = INITIAL_DATA[ACTUAL_SLIDE.value]
        ACTUAL_SLIDE.value += 1

    }, 5000);
});

</script>
  
<style scoped>
@keyframes fadeIn {
    from {
        opacity: 0;
    }

    to {
        opacity: 1;
    }
}

.animate-fade-in {
    animation: fadeIn 1s ease-out;
}
</style>
  