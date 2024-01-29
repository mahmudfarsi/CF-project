<script setup>
    import { defineProps } from 'vue';
    import { string,number, bool } from 'vue-types';

    defineProps({
        tag:string().def('div'),
        isWrap:bool().def(false)
    })
</script>


<template>
    <component :is="tag" :class="['row',`row--${isWrap ? 'wrap' : 'nowrap'}`]">
        <slot/>
    </component>
</template>



<style scoped>
    .row{
        width: 100%;
        display: flex;
        flex-direction: row;
    }

    .row--wrap{
        flex-wrap: wrap;
        background: cadetblue;
    }

    .row--nowrap{
        flex-wrap: nowrap;
        justify-content: space-between;
        align-items: center;
    }
</style>
