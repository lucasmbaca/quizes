<template>
    <header>
        <h4>Question {{ questionStatus }}</h4>
        <div class="bar">
            <div class="completion" :style={width:percentageBar}></div>
        </div>
    </header>
</template>

<script setup>
import { defineProps } from 'vue';

const {questionStatus, percentageBar} = defineProps(["questionStatus","percentageBar"])
</script>

<style scoped>
header {
    margin-top: 20px;
}

header h4 {
    font-size: 20px;
}

.bar {
    width: 300px;
    height: 50px;
    border: 3px solid bisque;
}

.completion{
    height: 100%;
    width:0%;
    background-color: bisque;
}
</style>