<script setup>
const props = defineProps(['doTheMath'])
</script>

<template>
    <div class="alert alert-secondary finalResult col-md-6" role="alert">
        {{ props.doTheMath }}
    </div>
</template>

<style scoped>
.finalResult {
    display: flex;
    justify-content: center;
    font-weight: bold;
    margin-top: 5px;
    font-size: large;
    margin: 15px auto;
}
</style>