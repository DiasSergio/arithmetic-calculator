<script setup>
import { reactive } from "vue";

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

    console.log(doTheMath())
}

</script>

<template>
    <div class="container">
        <header class="p-5 mb-4 mt-4 bg-light rounded-3">
            <h1>Calculator</h1>
            <p>
                Feel free to do the math.
            </p>
        </header>
        <form>
            <div class="row inputs">
                <div class="col-md-4">
                    <input required @keyup="e => status.firstValue = e.target.value" type="number"
                        placeholder="Enter your first value" class="form-control">
                </div>
                <div class="col-md-3">
                    <select @change="e => status.filter = e.target.value" class="form-control">
                        <option value="Math">
                            Do the math!
                        </option>
                        <option value="Addition">
                            Addition
                        </option>
                        <option value="Subtraction">
                            Subtraction
                        </option>
                        <option value="Division">
                            Division
                        </option>
                        <option value="Multiplication">
                            Multiplication
                        </option>
                    </select>
                </div>
                <div class="col-md-4">
                    <input required @keyup="e => status.secondValue = e.target.value" type="number"
                        placeholder="Enter your second value" class="form-control">
                </div>
            </div>
        </form>
        <div class="alert alert-secondary finalResult col-md-6" role="alert">
            {{ doTheMath() }}
        </div>
        <div class="links">
            <ul>
                <li>
                    <a href="https://github.com/DiasSergio" target="_blank"><img src="./components/icons/github.svg"
                            alt="github logo"></a>
                </li>
                <li>
                    <a href="https://www.linkedin.com/in/sergio-pereira-dias-junior-790557161/" target="_blank"><img
                            src="./components/icons/linkedin.svg" alt="linkedin logo"></a>
                </li>
            </ul>
        </div>
    </div>
</template>

<style scoped>
li {
    list-style: none;
}

a {
    padding: 10px;
    text-decoration: none;
}

img {
    max-width: 50px;
    width: 100%;
}

ul {
    display: flex;
    justify-content: center;
    padding-left: 0;
}

header {
    text-align: center;
}

.inputs {
    display: flex;
    justify-content: space-between;
    margin-bottom: 10px;
}

input[type=number]::-webkit-inner-spin-button,
input[type=number]::-webkit-outer-spin-button {
    -webkit-appearance: none;
    margin: 0
}

.finalResult {
    display: flex;
    justify-content: center;
    font-weight: bold;
    margin-top: 5px;
    font-size: large;
    margin: 15px auto;
}
</style>
