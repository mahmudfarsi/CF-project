<script setup>
    import { defineProps } from 'vue';
    import { number, oneOfType, string } from 'vue-types';


    defineProps({
        src:string().isRequired,
        alt:string().isRequired,
        height:oneOfType([number(),string().validate(v => !isNaN(+v))])
    })
</script>


<template>
    <div class="box">
        <img :src="src" :alt="alt" :height="height">
    </div>
</template>