<script setup>
    import { computed, defineProps, ref } from 'vue';
    import {string,shape, bool, number} from 'vue-types';
    import Card from '../Card.vue';
    import Img from '../Img.vue';
    import Button from '@/components/Button.vue'
    import Row from '@/components/Row.vue'

    const props = defineProps({
        country:shape({
            flags:shape({
                png:string().required,
                svg:string().isRequired,
                alt:string().isRequired
            }),
            cca2:string().isRequired,
            name:shape({
                common:string().isRequired,
                official:string().isRequired
            }),
            independent:bool().isRequired,
            region:string().isRequired,
            subregion:string().isRequired,
            population:number().isRequired
        })
    })
    const isFav = ref(false)
    const toggle = () => {
        isFav.value = !isFav.value
    }

    const calcPopulation = (number) => {
    const numberLength = number.toString().length

    let title = ''
    let count = number

    if (numberLength > 3 && numberLength <= 5) {
        title = 'thousand'
        count = number / 1000
    }
    else if (numberLength > 5 && numberLength <= 9) {
        title = 'million'
        count = number / 1000000
    } else if (numberLength > 9) {
        title = 'billion'
        count = number / 1000000000
    }

    let roundPow = 1
    const [countMain, countRemain] = count.toString().split('.')
    if (countMain === '0' || (countMain.length === 1 && countRemain?.length > 1)) {
        roundPow = 10
    }
    count = Math.floor(count * roundPow) / roundPow

    return `${count} ${title}`

}

    const description = computed(()=>{
        const name = props.country.name?.official;
        const independent = props.country.independent ? 'an independent country' : 'a dependent territory';
        const subrigion = props.country.subregion;
        const population = calcPopulation(props.country.population || 0)
      return  `${name} is ${independent} in ${subrigion} with an estimated population of over ${population} people.`
    })
</script>

<template>
    <Card tag="li" :is-simple="false" class="card-list">
        <template #header>
            <Img :src="country.flags.png" :alt="country.cca2" class="image" height="150"/>
        </template>
        <div class="body">
            <Row tag="div" :is-wrap="false">
                <h2 class="title">
                    {{ country.name.common }}
                </h2>
                <label class="label">
                    <Button :icon="isFav ? 'filled-heart' : 'empty-heart'" :is-icon-only="false" @click="toggle" tag="span" class="btn"/>
                    <input v-model="isFav" type="checkbox" class="input">
                </label>
            </Row>
            <p class="description">
                {{ description }}
            </p>
        </div>
    </Card>
</template>


<style scoped>

    .body{
        display: flex;
        flex-flow: column nowrap;
        width: 100%;
    }
    .title{
        flex-grow:1;
        background: khaki;


    }

    .label{
        background: cadetblue;
        position: relative;

    }
    .card-list{
        width: 25%;
        max-width: ;
    }
</style>