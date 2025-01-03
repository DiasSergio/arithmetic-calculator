<script setup>
import { reactive } from "vue";
import Header from './components/Header.vue';
import Form from './components/Form.vue';
import Results from './components/Results.vue';
import Footer from './components/Footer.vue';

const status = reactive({
    firstValue: 0,
    secondValue: 0,
    finalValue: 0,
    filter: false,
});

const addition = () => {
    status.firstValue && status.secondValue > 0 ?
        status.finalValue = parseInt(status.firstValue) + parseInt(status.secondValue) : status.finalValue = "Please insert valid values!"
    return status.finalValue
}

const subtraction = () => {
    status.finalValue = status.firstValue - status.secondValue;
    return status.finalValue
}

const multiplication = () => {
    status.finalValue = status.firstValue * status.secondValue;
    return status.finalValue
}

const division = () => {
    status.finalValue = status.firstValue / status.secondValue;
    return status.finalValue
}

const doTheMath = () => {
    const { filter } = status;

    switch (filter) {
        case 'Math':
            return 0
            break;
        case 'Addition':
            return addition()
            break;
        case 'Subtraction':
            return subtraction()
            break;
        case 'Division':
            return division()
            break;
        case 'Multiplication':
            return multiplication()
            break;
        default:
            return status.finalValue
            break;
    }
}

</script>

<template>
    <div class="container">
        <Header />
        <Form :edit-filter="e => status.filter = e.target.value"
            :edit-first-value="e => status.firstValue = e.target.value"
            :edit-second-value="e => status.secondValue = e.target.value" />
        <Results :do-the-math="doTheMath()" />
        <Footer />
    </div>
</template>
