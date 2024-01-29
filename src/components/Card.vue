<script setup>
    import { defineProps } from 'vue';
    import {bool, string} from 'vue-types';



    defineProps({
        tag:string().def('div'),
        isSimple:bool().def(false)
    })
</script>


<template>
    <component :is="tag" :class="['jCard',`jCard--${ isSimple  ? 'simple' : 'notSimple'}`]">
        <div v-if="$slots.header" class="j-card-header">
            <slot name="header"/>
        </div>
        <slot/>
        <div v-if="$slots.footer" class="j-card-footer">
            <slot name="footer"/>
        </div>
    </component>
</template>


<style scoped>
    .jCard{
        
    }

    .jCard--notSimple{
        display: flex;
        flex-direction: column;
        gap: 10px;
        align-items: center;
        padding: 20px;
        justify-content: center;
        border-radius: 10px;
        border: 1px solid var(--CardBorder, rgba(255, 255, 255, 0.50));
        background: var(--CardBg, rgba(255, 255, 255, 0.60));
        box-shadow: 0px 1px 0px 0px rgba(0, 0, 0, 0.05), 0px 4px 4px 0px rgba(0, 0, 0, 0.05), 0px 10px 10px 0px rgba(0, 0, 0, 0.10);
    }

    .jCard--simple{
        display: flex;
        flex-flow: row nowrap;
        justify-content: space-between;
    }
</style>