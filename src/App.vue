<template>
    <div>
        <div v-for="item in 10">
            <img :src="'./assets/images/' + item + '.png'" alt="">
        </div>
        <img src="./assets/images/1.png" alt="">
    </div>
</template>

<script setup>
     import {ref} from 'vue';

</script>

<style lang="less" scoped>

</style>