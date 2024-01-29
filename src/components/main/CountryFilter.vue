<script setup>
    import { defineProps,defineEmits, ref, computed } from 'vue';
    import {string} from 'vue-types';
    import Card from '@/components/Card.vue'
    import Button from '@/components/Button.vue'

    const props = defineProps({
        region:string()
    })
    const emits = defineEmits(['select-region'])
    const REGION = ['Asia','Africa','Europe','Americas','Antarctica','Oceania'];
    const filterOption = [
        {
            label:'all region',
            value:undefined
        },
            ...REGION.map(region => ({
                label:region,
                value:region,
            }))
    ]

    const isDropdownOpen = ref(false)
    const toggleDropdown = () => isDropdownOpen.value = !isDropdownOpen.value
    const dropdownTitle = computed(()=>{
        if(!props.region){
            return 'Region'
        }
        return filterOption.find(option => option.value === props.region)?.label
    })
    const onRegionSelect = (region)=>{
        toggleDropdown()
        emits('select-region',region.value)
    }
</script>


<template>
    <div>
        <Card :is-simple="true" class="btn-filter">
            <template #header>
                filer
            </template>
            <div>
                <Button @click="toggleDropdown" tag="button" icon="right-flesh" class="btn-main">
                    {{ dropdownTitle }}
                </Button>
            </div>
                <Card  v-show="isDropdownOpen" tag="ul" class="btn-li">
                    <li 
                        v-for="option in filterOption" 
                        :key="option.value"
                       
                        @click="onRegionSelect(option)">
                        {{ option.label }}
                    </li>
                </Card>
        </Card>
    </div>
</template>


<style scoped>
    .btn-filter{
        background-color: aquamarine;
        display: flex;
        position: relative;

    }
    .btn-main{
        
        cursor: pointer;
    }
    .btn-li{
        background: honeydew;
        display: flex;
        flex-direction: column;
        white-space: nowrap;
        position: absolute;
        top: 44px;
        cursor: pointer;
    }
</style>