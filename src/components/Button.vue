<script setup>
    import { defineProps } from 'vue';
    import {bool, oneOf, string} from 'vue-types'
    import Icon from '@/components/Icon.vue'


    defineProps({
        icon:string(),
        isIconOnly:bool().def(false),
        tag:oneOf(['button','a','span']).def('button')
    })
    
</script>


<template>
    <component :is="tag" :class="['btn',`btn--${ isIconOnly ? 'simple' : 'noSimple' }`]">
        <slot v-if="!isIconOnly"/>
        <Icon v-if="icon" :name="icon"/>
    </component>
</template>