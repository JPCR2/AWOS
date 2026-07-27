<!--Estructura SFC(3 Partes: HTML, JS y CSS)-->
<script setup>
//1. Importamos: otros cmponentes, librerías, etc
import { ref, computed, onMounted } from 'vue'  
import { useWeatherStore } from '@/Stores/weatherStore'

//2. Estados locales - Solo Datos que este componente necesita
const extra = ref(false)

//3. Estado global - desde el store de pinia
const store = useWeatherStore() 

//4. Valores computados - Derivados del estado de datos en nuestro store
const iconClima = computed(() => store.temperatura>25?'-':'+')

//5. Ciclo de vida 
onMounted(() => console.log('componente listo'))
</script>
<template>
    <div class="weather-card">
        <span class="icon">{{ iconClima }}</span>
        <p>{{ store.temperatura }}°C</p>
        <button class="masinfo" @click="extra = !extra">
            {{ extra ? 'Menos info...' : 'Más info...' }}
        </button>
        </div>
</template>
<style scoped> 
/* Scoped = estilos que se aplican solo a este componente */
.weather-card{
    padding: 24px;
    border-radius: 12px;

}
</style>

