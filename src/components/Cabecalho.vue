<script setup>
    const props = defineProps(['historico']);
    
</script>

<template>
    <header class="p-5 mb-2 mt-4 rounded-3 image" >
        <h1 class="text-lg-end text-light">Calculadora VueJS</h1>
        <p v-if="props.historico != ''" class="text-sm-end text-light">Histórico: {{ props.historico }} </p>
    </header>
</template>

<style scoped>

    header {
        height: 20vh;
    }

    .image {
        background-image: url('../assets/calculadora_fundo_3.jpg');
        background-size: cover;

        
    }

    

</style>