<script setup>

</script>


<template>
    <div class="container">
        <slot/>
    </div>
</template>


<style scoped>
    .container{
        width: 100%;
        --max-width:100%;
        max-width: var(--max-width);
        min-height: 100vh;
        display: flex;
        flex-flow: column nowrap;
    }

    @media screen and (max-width:720px){
        .container{
            padding: 0px 20px;
        }
    }

    @media screen and (min-width:720px) and (max-width:1200px){
        .container{
            --max-width:720px;
        }
    }

    @media screen and (min-width:1200px) and (max-width:1400px) {
        .container{
            --max-width:1140px;
        }
        
    }

    @media screen and (min-width:1400px) {
        .container{
            --max-width:1320px;
        }
    }
</style>